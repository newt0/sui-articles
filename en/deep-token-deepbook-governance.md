[The DEEP Token's Role in DeepBook Governance](https://blog.sui.io/deep-token-deepbook-governance/)

## MEV on Sui: Current State and Next Steps

How MEV works on Sui—mechanisms for transaction ordering, protection, and fair competition.

* [![Mysten Labs](https://blog.sui.io/content/images/size/w100/2023/11/MystenLabs_Logomark_Red-4.png)](https://blog.sui.io/author/mysten/)

![MEV on Sui: Current State and Next Steps](https://blog.sui.io/content/images/size/w2000/2025/02/02-49-Blog-Header.png)

Maximum extractable value (MEV) has become a big topic in the blockchain industry, as it deals with transaction ordering and arbitrage opportunities. In the interest of ensuring transparency, protecting transactions, maintaining a healthy network, and rewarding participants, we have been thoughtfully implementing Sui improvement proposals (SIPs) and other mechanisms to guide MEV on Sui. 

Along with current mechanisms, we plan on building more to ensure our high-level principles guide the evolution of MEV on Sui.

## Design principles and considerations

Every trade on Sui introduces new information with potential profit opportunities. The MEV ecosystem on Sui is shaped via several mechanisms:

1. Mechanisms for **submitting MEV transactions**.
2. Mechanisms for **disseminating MEV opportunities**.
3. Mechanisms for **distributing MEV revenue**.
4. Mechanisms for **protecting user transactions.**

Our general priorities are as follows:

1. User **transaction protection** is more important than the amount of extracted value. Prioritize smaller slippage over larger extracted value. Avoid out-of-protocol auctions that increase latency with no way to opt out.
2. **Network transparency** is preferable over offline deals with validators or relayers.
3. Prioritize competition via **priority gas auctions (PGAs)** and discourage spamming behaviors leading to system inefficiencies: a perfect system we’re striving for makes the dominant strategy for a searcher to send a transaction with a priority fee determined by the extracted value.
4. Encourage **rewards distribution** to ecosystem-aligned participants: the validators, stakers, apps, and users.

## Transaction submission

Since transactions that modify the same object are executed sequentially, clients compete to increase the chances of their execution order. From a system’s perspective, **priority gas auctions (PGAs)** are an efficient way to allocate resources and prevent spam while redistributing gas fees across participants.

The key driver of priority gas auctions is **quantized execution**:

* Transactions that are ordered by consensus are processed in blocks. Traders compete for priority orders both **within** and **across** commits via gas auctions.
* This contrasts with CEX market makers, where execution priority depends purely on speed, achieved through low-latency networking and algorithms.
* A higher consensus commit rate **reduces quantization effects**, making DEX execution more efficient but narrowing the PGA window.
* Currently, PGAs of the non-congested objects matter for the fastest searchers only. With a **15 commits/sec** Sui rate, a 70 millisecond advantage in transaction submission speed is a deal breaker.
  * Congested objects might defer transaction execution, which amplifies the importance of PGAs, since the window of the competing transactions is growing to potentially 10 times that of a regular consensus commit. 

There are two separate mechanisms for steering transactions towards specific upcoming Sui commits:

### Submitting a batch of transactions within a soft bundle: [SIP-19](https://github.com/sui-foundation/sips/blob/main/sips/sip-19.md?ref=blog.sui.io)

1. Transactions submitted via a soft bundle are included in the same consensus commit with a high probability for valid bundles. Bundle validity conditions require, among others, identical gas prices for all its transactions.
2. In practice, this mechanism enables offchain auctions for bundling the original transaction with its back-run transactions, e.g., the one run by [Shio](https://www.getshio.com/explorer?ref=blog.sui.io).

### Prioritizing transaction via consensus amplification: [SIP-45](https://github.com/sui-foundation/sips/blob/main/sips/sip-45.md?ref=blog.sui.io)

1. SIP-45 is tackling the problem of potential jitters in consensus submission, where a transaction with a higher gas price is ordered in a later commit than one with a lower gas price submitted at the same time.
2. There are two natural jitter sources in consensus submission:
   1. A submitting validator is behind by a couple of consensus rounds: a transaction that is submitted by another validator might get ordered first.
   2. A validator who is a leader of the consensus round has a one-round advantage over any other validator submission.
3. SIP-45 amplifies consensus submission for the gas prices that are higher than k x RGP (k is a system parameter that is set to 5 in the current configuration, and RGP is reference gas price). A transaction with a gas price of n x RGP is amplified n times.
4. The **broader adoption of SIP-45** by both the app builders and the users creates a more efficient system with fair competition.
   1. It’s important to note that SIP-45 doesn’t change the fundamental system properties from the client perspective: **it disincentivizes spamming** by providing a more efficient alternative.

### Choosing the right gas price for a transaction

There are two major factors a client should consider to determine the gas price of a submitted transaction:

1. **Priority gas auction.**
   * Within the consensus commit, transactions modifying the same object are **ordered by their gas price**, which creates fair competition across the searchers.
2. **Consensus submission amplification.**
   * As described above, the gas price over 5 x RGP **amplifies consensus submission** with n validators submitting the given transaction to consensus. Any gas price increase beyond the amplification threshold is reducing the probability of low-performer submission jitters. In practice, an amplification factor of 5 is enough for eliminating jittering, while the gas price of 100 x RGP unlocks the next round’s leader submission with high probability.
3. **Avoiding congestion deferrals and cancellations.**
   * Sui limits the wall clock time of checkpoint execution via controlling the rate of transactions modifying the same shared object. Transactions modifying a congested object are ordered according to their gas price, with the lower-priced transactions being deferred and ultimately canceled in order to limit the longest chain of sequential execution per checkpoint, a mechanism called [**object-based local fee markets**](https://docs.sui.io/guides/developer/advanced/local-fee-markets?ref=blog.sui.io). *(Note that while gas prices might surge for shared objects providing high arbitrage opportunities, they remain unchanged for the rest of the system.)*
   * Full Nodes keep track of the gas prices of both the executed and the cancelled transactions mutating congested objects. The **results of a transaction dry-run** can therefore include both the lowest-priced-executed and the highest-priced-cancelled transaction gas prices for the congested objects modified by a given request. With this information, a client can determine the gas price required to avoid the deferral with high probability. *(Note, this work is just partially implemented and is going to be part of SDK within the next two months.)*

## Disseminating transaction information

Each transaction on Sui introduces information with potential profit opportunities. Consider a happy-path lifecycle of a shared object transaction since the moment it’s submitted by the client until its effects are observed by a third party:

![](https://blog.sui.io/content/images/2025/02/mermaid-diagram-2025-02-25-130957--1-.png)

1. A client submits a transaction to an RPC full node (typically chosen by the app).
2. RPC node broadcasts a transaction to the validators, which verify its validity and sign it, RPC node assembles transaction certificate from the quorum.
3. RPC node broadcasts transaction certificates to the validators.
4. A deterministically chosen validator submits the transaction to consensus. Mysticeti consensus is broadcasting the blocks between the validators, and in 3 consensus rounds, the block with the given transaction is committed.
   1. The transaction is executed on each validator
5. The transaction effects certificate is sent back to the RPC node and the client.
6. Within 1 to 3 consensus rounds each validator forms and signs a checkpoint (checkpoints are batching several consensus commits).
7. Checkpoint signatures are broadcasted between the validators and each validator forms a checkpoint certificate.
8. A state-sync protocol is responsible for disseminating certified checkpoints in a p2p fashion. Typically each validator has a direct peer that is not serving RPC requests: a state-sync full node, which receives their checkpoint first.
9. A third-party full node that is connected to the state-sync full node learns about the checkpoint and downloads its content. At this moment we assume a third party that is directly connected to the full node can post-process the effects of this transaction and react accordingly.

### Disseminating transaction information before validator submission

As described in the previous section, there are Sui offchain auctions for submitting soft bundles following [SIP-19](https://github.com/sui-foundation/sips/blob/main/sips/sip-19.md?ref=blog.sui.io). These auctions intercept transaction submission via **offchain agreements between the apps and the auction system**, e.g., the one run by [Shio](https://www.getshio.com/explorer?ref=blog.sui.io).

This type of information dissemination assumes a well-behaved auction system that protects user transactions from potential sandwich attacks. Shio is incentivized to protect user transactions to maintain their business and therefore employs a number of auction techniques (bait transactions, random delays) to hurt the financial profitability of potential sandwich bots.

Obviously, this type of information dissemination happens outside of Sui (between the apps and the auction), is opt-in for the apps and the users, provides speculative information only, with no guarantee that the original user transaction is going to succeed.

### Streaming consensus blocks

In order to democratize low-delay access to the user transactions we’re designing a system for direct streaming of consensus blocks. At a high level, full nodes are going to have an option to directly subscribe to consensus blocks.

This way, full nodes will have an option to speculatively notify about the transactions that are to be committed with high probability. The network topology is using a standard open state-sync peer discovery protocol.

The speculative notification has the potential to significantly shortcut the propagation delay about the transaction to just about 160 milliseconds (2 consensus rounds) since validator submission.

The consensus block streaming project is currently in the design phase and we’re expecting to have a SIP within the next 1 to 2 months.

## Protecting user transactions

User transactions need to be protected against predatory front-running, sandwiching, and involuntary submission delays.

### External quorum driving

Sui transaction submission requires external quorum driving, which is typically executed by the full nodes.

![](https://blog.sui.io/content/images/2025/02/image.png)

In case a validator that receives a transaction submission request for transaction t wants to initiate a new transaction t', it is going to be behind the original quorum driver in the certificate assembly process. Unless the submitting full node is poorly connected to the Sui quorum, a validator that starts quorum driving t' in response to the original transaction, will assemble its certificate after t.

Furthermore, since t’s consensus submission is decentralized, it cannot be reliably postponed once its certificate reaches the quorum. Hence, if t's certificate reaches Sui quorum before the certificate of t', t is going to be settled before t' with high probability.

Therefore, the very fact of external quorum driving provides a natural front-running protection, assuming trust in the full node responsible for the transaction submission (since front-running predatory attempts are easily detected onchain, these attempts would be noted by the clients and hurt the RPC operator reputation).

### Mysticeti fast path

We’re currently working on a project that changes transaction submission to the fast path protocol described in the Mysticeti [paper](https://arxiv.org/abs/2310.14821?ref=blog.sui.io). According to this protocol, a user transaction can be submitted to a single validator, which would leverage Mysticeti for gathering and executing transaction certificates. While making the system significantly more efficient, it opens up front-running opportunities for the validator to receive the user transaction.

This risk is purely hypothetical since we don’t have any evidence of front-running attempts on Sui today. In a new setup, the possibility of a front-run is higher, but on the other hand, given deterministic knowledge about the submitting validator, it makes it easier to hold them accountable.

## Sui’s evolving MEV landscape

Sui’s MEV landscape is still taking shape, with new mechanisms coming later this year. While priority gas auctions and consensus amplification define the current system, upcoming innovations like time-lock encryption and Mysticeti’s fast path will reshape transaction execution and security. As these pieces come online, MEV on Sui will continue to evolve, creating a more dynamic and transparent ecosystem.
