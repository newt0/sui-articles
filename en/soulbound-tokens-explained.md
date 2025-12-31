[All About Soulbound Tokens](https://blog.sui.io/soulbound-tokens-explained/)

[Coined](https://vitalik.eth.limo/general/2022/01/26/soulbound.html?ref=blog.sui.io) by Ethereum co-founder Vitalik Buterin, a Soulbound token (SBT) is an NFT designed to be permanent and non-transferable. Unlike typical NFTs, which can be freely traded, SBTs remain bound to their original account, much like how skills or accomplishments in a game are tied to an individual user or account and cannot be transferred or traded. SBTs are useful in representing a person's identity, credentials, or achievements in the digital world.

The potential applications for SBTs are vast, ranging from verifiable credentials and reputation systems to more nuanced forms of governance and asset management. By providing a way to represent non-transferable attributes onchain, SBTs could revolutionize how we approach digital identity, professional certifications, and even social credit systems in decentralized environments.

## Technical implementation of SBTs on Sui

To make an NFT non-transferrable on Sui, thereby creating an SBT, developers can leverage Sui's object-centric data model. The primary step to create an SBT on Sui is to [remove the `store` ability from the NFT structure](https://docs.sui.io/concepts/transfers/transfer-to-object?ref=blog.sui.io#soul-bound-example). This crucial modification prevents the token from being freely transferred to other addresses using Sui's standard transfer functions.

When an object lacks the `store` ability, only the module that defined the object can transfer it, using the `sui::transfer::transfer` function. This restriction allows developers to implement [custom transfer rules](https://docs.sui.io/concepts/transfers/custom-rules?ref=blog.sui.io), providing fine-grained control over how and when the token can be transferred, if at all. By combining these features, developers can create tokens that exhibit the non-transferrable nature characteristic of SBTs, while still maintaining flexibility in defining specific behaviors as required by their use case.

### Sui allows SBTs to evolve

One of the standout features of SBTs on Sui is their ability to incorporate dynamic properties through [Sui's dynamic fields](https://docs.sui.io/concepts/dynamic-fields?ref=blog.sui.io). This functionality allows Sui NFT attributes to be modifiable after initial creation. As a result, SBTs can evolve based on creator decisions, user actions or achievements, changes in a user's status or credentials, and adapt to new use cases without requiring a new token. This dynamic capability enhances the utility of SBTs, making them more relevant and valuable over time.

[Sui's object display standard](https://docs.sui.io/standards/display?ref=blog.sui.io) complements SBTs by providing opportunities for enhanced visualization and interaction with these non-transferrable tokens. The display standard can be utilized to create custom visualization logic for SBTs, ensuring that their unique properties and dynamic nature are accurately represented in user interfaces. By combining these features, developers can create SBTs on Sui that are not only non-transferrable but also dynamic and adaptable, opening up new possibilities for various use cases.

## Case studies of SBTs on Sui

### Token allocations: DeepBook and NS

[DeepBook](https://www.deepbook.tech/?ref=blog.sui.io), Sui's native liquidity layer, and [SuiNS](https://suins.io/?ref=blog.sui.io), the premier name service on Sui, have both utilized SBTs as a way to provide clear token allocations to users before token generation.

[DeepBook's DBClaimNFT](https://blog.sui.io/deepbook-deep-token-launch/) serves as a soulbound claim ticket for the upcoming DEEP token launch. This innovative approach ensures that early supporters and community members have a verifiable, non-transferable right to claim tokens upon launch. Similarly, SuiNS employed SBTs for its [upcoming plans to decentralize](https://www.mystenlabs.com/blog/decentralization-of-suins?ref=blog.sui.io), further establishing the use of SBTs as a valuable tool for distribution strategies.

The use of SBTs for token allocations opens up exciting possibilities for project governance and community engagement before a token's official launch. For example, projects could use SBTs to grant early governance rights, allowing token holders to participate in a formal decision-making process and shape the project's direction even before a token is live.

### SuiLink 

[SuiLink](https://www.suilink.io/suilinks?ref=blog.sui.io) leverages SBTs to create cross-chain identity verification. By issuing SBTs on Sui, SuiLink establishes a direct, verifiable link between a user's Ethereum or Solana address and their Sui address. This implementation of SBTs creates an onchain representation of user identities across multiple blockchain ecosystems. This approach shows the potential of SBTs in enhancing interoperability, potentially facilitating more secure and reliable cross-chain interactions.

### SuiPlay0X1 purchases

[SuiPlay0X1](https://www.suiplay0x1.com/?ref=blog.sui.io) leveraged SBTs to represent [pre-order purchases](https://www.preorder.suiplay0x1.com/?ref=blog.sui.io) of their physical devices. This application demonstrates how SBTs can bridge the gap between digital and physical assets while ensuring certified reservation and uniqueness onchain. Each pre-order is represented by an SBT, creating a digital twin of the physical device reservation.

Notably, the first 1,000 pre-order customers received special edition SBTs with distinct visual representations, adding an extra layer of exclusivity. Furthermore, each SBT is sequentially numbered to correspond with the order of purchase, so the 1,001st buyer received an SBT prominently displaying "#1001". This numbering system not only verifies the order of purchase but also creates a sense of community and status among early adopters.

![](https://blog.sui.io/content/images/2024/09/0xb7d41d85e5a889099ba0af3cf6cecf5a3e4d653b5ca1191f4630609f2b51da88--1--1.svg)

![](https://blog.sui.io/content/images/2024/09/0x8051c4de176889ab41ee6ceb3371a843a8060016566785716ac13b0ba29488d7-3.svg)

The appearance of SuiPlay0X1 NFTs varies based on whether they are among the initial 1,000 or not.

By using SBTs for these pre-orders, SuiPlay0X1 ensures that each reservation is uniquely tied to its original purchaser, preventing unauthorized transfers or resales of pre-order rights. This approach highlights how soulbound tokens can add value and significance to digital representations of physical items, especially in contexts where the non-transferability of the right or reservation is crucial to maintaining fairness and authenticity in the distribution process.

## SBTs for tomorrow

Unlike static SBTs on other platforms, Sui's implementation allows these tokens to evolve over time, adapting to changing circumstances and user interactions. This flexibility opens up exciting possibilities beyond the uses currently seen with DeepBook, SuiNS, SuiLink, and SuiPlay0X1.

Looking ahead, we can envision SBTs impacting areas such as event ticketing, gaming achievements, and intellectual property protection. As the broader ecosystem grows, the dynamic capabilities of SBTs on Sui will play a crucial role in shaping new forms of digital identity and ownership, paving the way for innovative apps that we've yet to imagine.
