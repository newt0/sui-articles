[The Deflationary Nature of Sui’s Storage Fund](https://blog.sui.io/sui-storage-fund-deflationary/)

## The Deflationary Nature of Sui’s Storage Fund

Sui’s storage fund quietly turns every transaction into a force for sustainability and scarcity.

![The Deflationary Nature of Sui’s Storage Fund](https://blog.sui.io/content/images/size/w2000/2025/09/09-11-Blog-Header.jpg)

Sui’s storage fund sits at the core of the network’s design, quietly shaping the supply of SUI with every transaction. It’s the underlying mechanism that steadily [removes tokens from active circulation](https://sui.io/deflation?ref=blog.sui.io) while covering the long-term cost of storing onchain data. 

Unlike staking or bridging, which temporarily lock tokens, the storage fund ensures that network activity pulls SUI out of active circulation permanently, adding deflationary pressure to SUI.

For users, this mechanism is more than just bookkeeping. Storage costs are covered up front, keeping network operations sustainable as storage demands increase. At the same time, the steady removal of SUI from circulation makes the token increasingly scarce as activity grows, tying the growth of the network directly to its long-term value.

## What is Sui’s storage fund?

[Sui’s storage fund](https://blog.sui.io/storage-fund-demystified/) is a pool of SUI set aside to subsidize the long-term storage of data on Sui. It is staked across active validators in proportion to their stake weight, generating rewards that offset the burden of storage. This ensures that the cost of maintaining data falls on those who require it, while strengthening the sustainability of Sui’s infrastructure.

Whenever users create or modify objects, they pay a [storage fee](https://blog.sui.io/storage-fees-explained/). Since nearly every transaction increases storage requirements, nearly every transaction on Sui funnels SUI into the fund.

That fee has two parts:

* **Refundable deposit**: Locked in the storage fund for as long as the object exists. If the object is deleted or slimmed down, a prorated portion of the deposit is returned.
* **Non-refundable fee**: Permanently absorbed by the storage fund. This portion is never returned, removing that SUI from active circulation forever.

## How the storage fund creates deflationary pressure

This design makes the storage fund the most powerful deflationary mechanism in Sui. Here’s why:

1. **Non-refundable storage fees**: Every time an object is created or modified, part of the payment stays permanently in the storage fund, removing that SUI from active circulation permanently.
2. **Mutable object deposits**: For as long as an object exists, its deposit is frozen. Some may eventually be released if an action decreases their storage requirement, but many remain locked indefinitely.
3. **Immutable object deposits**: Because immutable objects can never be changed or deleted, both their fee and deposits are never returned. That SUI is effectively removed from circulation forever.

Together, these dynamics mean that nearly every transaction contributes to scarcity, locking or permanently removing SUI from circulation.

[Walrus](https://www.walrus.xyz/?ref=blog.sui.io), the decentralized storage network, has a unique tie to this process. Each time a blob is stored on Walrus, it generates a mutable object on Sui that records the blob’s metadata. These objects draw SUI into the storage fund just as any other object on Sui would. As Walrus adoption grows, so does the volume of these objects, creating an additional source of deflationary pressure on SUI.

In this way, adoption of both Sui and Walrus naturally reinforces scarcity. More transactions and more stored data mean more SUI consistently pulled out of circulation, strengthening the link between ecosystem growth and long-term value.

## The numbers today

According to [SuiScan](https://suiscan.xyz/mainnet/analytics/storage%20info?ref=blog.sui.io), the storage fund currently holds 1.95 million SUI. In just over two years of mainnet, nearly 700,000 SUI are gone forever, and another 1.2 million are effectively frozen. That’s already a meaningful deflationary impact and grows stronger with every new user and application.

![](https://blog.sui.io/content/images/2025/09/data-src-image-4bd47bf4-1a0d-49ee-8a5e-5288036976da.png)

Caption: The storage fund balance has climbed steadily, pulling SUI out of circulation to make data storage more sustainable.

## Sustainable scarcity

Because SUI’s supply is capped, the storage fund creates ongoing downward pressure on the available supply of tokens. This isn’t speculative; it’s a structural feature of the network. Transactions, NFT mints, and contract deployments all trigger the same outcome, removing more SUI from the active supply by either locking or permanently removing it.

The result is a self-reinforcing loop: adoption funds sustainability while also reinforcing scarcity. Sui can scale without ballooning storage costs for validators, and token holders benefit from a system that continuously siphons SUI out of circulation.

## Setting Sui apart

The storage fund is more than a technical detail of Sui’s tokenomics, it’s a core driver of scarcity and sustainability. By linking storage fees directly to usage, it ensures that ecosystem growth naturally translates into deflationary pressure.

With nearly 2 million SUI already locked in the storage fund and close to 700,000 permanently removed from active circulation, the deflationary nature of SUI is already visible. But what truly sets Sui apart is that this mechanism is built into the core of the network itself, aligning scalability, sustainability, and value creation in a way that no other blockchain does.
