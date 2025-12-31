[Mysticeti v2: Faster and Lighter Sui Transaction Processing](https://blog.sui.io/mysticeti-v2-sui-consensus/)

*Written by: Tasos Kichidis (Software Engineer), Lefteris Kokoris-Kogias (Research Scientist), Arun Koshy (Software Engineer), and Maxwell Tian (Software Engineer).*

[Mysticeti](https://sui.io/mysticeti?ref=blog.sui.io) is the consensus protocol that powers Sui. First launched on mainnet in July 2024, it introduced a new generation of high-performance consensus built on [Directed Acyclic Graphs (DAGs)](https://blog.sui.io/all-about-directed-acyclic-graphs/). This design allowed Sui to achieve industry-leading responsiveness, low latency, and scalability.

**With Mysticeti v2, we are taking the next major step forward.** 

This version integrates transaction validation directly into the consensus process, removing redundant steps that previously added compute cost and latency. It also introduces a more efficient client mechanism called Transaction Driver, which simplifies how transactions are submitted and confirmed on the network. 

These updates make transaction processing significantly faster, lighter, and more resilient, realizing the full performance potential that Mysticeti was designed for.

## The evolution of DAG-based consensus

To understand what has changed and why these improvements matter, it helps to look at how DAG-based consensus protocols have evolved over time.

### Traditional consensus protocols

Validators take turns proposing blocks and transactions. There are tradeoffs between consensus throughput, latency, and validator committee size.

*Example: Tendermint, Hotstuff.*

### Mempool and consensus on a certified DAG

Every validator proposes blocks containing transactions almost continuously. Blocks are first certified, then committed. This decouples transaction dissemination from ordering and sustains throughput even as the validator set scales. Parallel proposing also improves censorship resistance by making it harder for a subset of validators to deny transactions from being submitted to consensus.

*Example: Narwhal & Bullshark.*

### Consensus on an uncertified DAG

Uncertified-DAG protocols drop the certification step to further reduce algorithmic complexity and the number of rounds needed to commit blocks.

*Example: Mysticeti.*

Mysticeti has been very successful in providing a responsive user experience on Sui. Although Mysticeti achieves the lowest possible consensus latency under its operating model, its integration with Sui has not yet delivered its full potential.

In Sui transaction processing, there is an additional pre-consensus step where validators vote on whether a transaction should be accepted into consensus. Transactions can be denied for various reasons—from using stale input data to attempting to publish invalid Move packages.

A transaction can only execute with votes from more than two-thirds of validators by stake (a quorum). This step gives the Sui validator committee the power to filter transactions (since more than one-third of votes by stake can deny a transaction) without requiring identical actions from all validators.

This mechanism also supports the “fastpath” on Sui, where transactions that touch only owned objects can be finalized faster without requiring consensus. The downside, however, is that this pre-consensus step adds significant compute cost for the validation of each transaction and increases latency for non-fastpath transactions as well.

We have been working on merging this step into Mysticeti and eliminating all of its associated costs. The [Mysticeti paper](https://docs.sui.io/paper/mysticeti.pdf?ref=blog.sui.io) introduced the **Mysticeti-FPC** protocol, which removed the extra compute cost. After Mysticeti v1 launched, we focused on eliminating the latency overhead as well. This work culminates in **Mysticeti v2**, which realizes the full performance promise of Mysticeti and supports all capabilities needed by the Sui network.

## How Mysticeti v2 works

Mysticeti v2 is an enhancement on top of Mysticeti v1, not a replacement. 

In Mysticeti, one or more leader or anchor blocks are selected in each round. Running the “commit rule” over the DAG decides if an anchor should be committed or skipped. Then, uncommitted blocks connected by the newly committed anchor form the new commit.

The commit rule does not change between Mysticeti v1 and v2. To commit an anchor block, the most common case is when there is a quorum (more than two-thirds of committee stake) of certificates, where each certificate has a quorum of votes for the anchor. This is called a *direct commit*. Another case is an *indirect commit*, where there is at least one certificate pointing to an earlier anchor (round R) in blocks connected by a later (round ≥ R+3) directly committed anchor.

![](https://blog.sui.io/content/images/2025/11/data-src-image-87cbc881-7ec4-4b58-9028-41ca8b8baa8a.png)

Mysticeti’s DAG consensus: validators propose, vote, and certify blocks to form verifiable certificates.

In Mysticeti v2, conceptually, the Mysticeti leader commit rule is extended to apply on every transaction concurrently. Each transaction is finalized or rejected, while blocks are decided to be committed or skipped on the same DAG.

A transaction is finalized if it has a quorum of finalization certificates. Each finalization certificate block is connected to a quorum of earlier-round blocks that accept (vote for) the transaction. Unlike the Mysticeti commit rule, blocks that vote for or certify a transaction can be in rounds much later than the block containing the transaction.

Another way to finalize a transaction is similar to indirect commit—when a certificate of the transaction is included in committed blocks. When a transaction observes a quorum of reject votes, it is rejected. If a transaction *T* is not finalized after observing a commit *C₂* with its anchor three or more rounds after the initial commit *C₁* that includes the transaction, *T* is also rejected.

However, a naive implementation of the Mysticeti v2 algorithm would not scale to processing 500,000 transactions. Having validators cast explicit votes on every transaction would amplify network traffic and reduce overall throughput. Evaluating whether each transaction has a quorum of certificates would also be computationally expensive, and block propagation across the network can be uneven.

We optimized the Mysticeti v2 algorithm to address these challenges. Validators now cast explicit votes **only** for rejections. Accept votes are implicit through ancestor block links. Transaction certifications are evaluated only when necessary. The protocol also allows multiple rounds to vote and certify a transaction, ensuring that valid transactions can still be finalized even if submitted via a validator with a weak network connection.

## Transaction Driver: A more efficient transaction client

With Mysticeti v2, transaction submission to a validator becomes less complicated and more efficient.

**Quorum Driver** was the original mechanism for submitting transactions to Mysticeti v1. It worked by broadcasting every transaction to all validators for certification, collecting BLS signatures on each transaction’s validity. After signature aggregation, it re-broadcasted the certified transaction for consensus submission and gathered execution results from all validators again.

While this design was necessary for the original, consensus-less fastpath, it came with a high CPU cost—at least two-thirds of validators (by stake) had to sign every transaction—and heavy bandwidth usage, as each transaction was broadcast twice.

**Transaction Driver** solves these issues while preserving fast finality. It leverages the new transaction certification path introduced by Mysticeti v2 to achieve the same goals with far less overhead.

Key improvements include:

1. **Minimal validator signatures**: Validators now sign transaction validity as part of consensus block signing, batching multiple transactions together rather than signing each individually. This dramatically reduces CPU load.
2. **Single-path submission**: The client now submits each transaction to a single chosen validator instead of all validators, retrieving one complete copy of the effects. This reduces network usage to near-optimal levels.
3. **Smart validator selection**: The driver automatically selects validators based on historical end-to-end latency for faster confirmations.
4. **Graceful retries and resilience**: If the selected validator is slow or offline, the client automatically retries with others, targeting at least one-third of validators by stake. Errors are classified as retriable or non-retriable, maximizing the likelihood of successful completion before feedback is returned.
5. **Bandwidth protection and DoS resistance**: Transaction Driver integrates with validator-side protections to prevent spam or bandwidth amplification attacks.

Transaction Driver achieves this by sending a transaction to a selected validator, receiving its position in consensus, and then using the transaction digest and consensus position to retrieve and certify its full effects with a quorum of validators.

## Rollout

Transaction Driver has been enabled for all traffic on full nodes operated by Mysten Labs and several partner teams. We observed a **35% latency reduction** on Asia-based full nodes (from ~1.00s to ~0.65s) and a **25% reduction** on Europe-based full nodes (from ~0.55s to ~0.40s).

![](https://blog.sui.io/content/images/2025/11/data-src-image-1deaed49-063b-48f6-b9db-2f6a8db04bca.png)

Latency comparison on Asia-based full nodes showing improved performance with Transaction Driver (yellow) versus Quorum Driver (green)

![](https://blog.sui.io/content/images/2025/11/data-src-image-74aeb7b0-3d20-4ab0-813d-9f37519f3bb6.png)

Latency comparison on Europe-based full nodes showing improved performance with Transaction Driver (yellow) versus Quorum Driver (green).

Starting with **Sui node v1.60**, Mysticeti v2 and Transaction Driver will become the default for transaction processing.

## Additional changes

Several other improvements introduced as part of Mysticeti v2 were rolled out earlier and will be covered in future blog posts, including:

* **Garbage collection:** Old consensus blocks are dropped instead of being committed, limiting the performance impact of validators that fail to propagate their blocks efficiently.
* **Smart ancestor selection:** Validators that do not broadcast blocks consistently are excluded as ancestors for linking.

## **Future Work**

The work to improve Sui consensus is ongoing. 

The next phase focuses on reducing the median number of message rounds needed to commit transactions (from four down to three), further improving throughput and responsiveness.

Another key goal is enabling consensus blocks to stream directly to full nodes, giving them access to uncommitted transactions and reducing end-to-end latency even further. 

In parallel, efforts are underway to prevent owned-object “deadlocks” at the protocol level, ensuring seamless transaction execution across all object types.

We look forward to sharing more updates as these projects progress.
