[Sui Stack Messaging SDK: Programmable Communication for Web3](https://blog.sui.io/sui-stack-messaging-sdk/)

## Sui Stack Messaging SDK: Programmable Communication for Web3

Build private, programmable communication directly into your app with the new Sui Stack Messaging SDK.

![Sui Stack Messaging SDK: Programmable Communication for Web3](https://blog.sui.io/content/images/size/w2000/2025/09/07---01-Blog-Header--1-.png)

The [Sui Stack Messaging SDK](https://github.com/MystenLabs/sui-stack-messaging-sdk?ref=blog.sui.io) is now available in alpha. This new developer toolkit makes secure, programmable communication a native part of building on Sui. 

For years, messaging in crypto has been fragmented. Builders have relied on centralized apps and APIs to connect with users, leaving conversations vulnerable to phishing and disconnected from wallet activity. The Messaging SDK changes this by bringing verifiable, encrypted communication into the same stack that already powers assets, storage, and access control.

The Messaging SDK is designed to work seamlessly with the [Sui Stack](https://x.com/SuiNetwork/status/1945910251720720794?ref=blog.sui.io), combining the strengths of the [Sui blockchain](https://sui.io/?ref=blog.sui.io), [Walrus decentralized storage](https://walrus.xyz/?ref=blog.sui.io), and [Seal decentralized secrets management](https://seal.mystenlabs.com/?ref=blog.sui.io). By tying messaging into these building blocks, it creates a foundation for communication that is private, recoverable, and composable.

## Why we need a secure messaging primitive in Web3

For all the innovation in Web3, one thing has been missing: a native, privacy-preserving way for users and apps to communicate. Without a secure, onchain messaging primitive, builders are forced into workarounds that rely on centralized APIs, middleware, custom integrations, and off-chain apps. These approaches undermine both user trust and product experience.

The result is fractured conversations, business support handled on external platforms, and sensitive conversations that lack both verifiability and cross-device recoverability. A truly Web3-native messaging layer has to do more: link wallets with an onchain identity, guarantee encryption, and integrate directly with onchain activity.

This is exactly what the Sui Stack Messaging SDK is designed to deliver. By integrating messaging into the Sui Stack, the SDK gives developers a way to build communication directly into their apps. Unlike siloed or closed messaging systems, it enables builders to plug messaging into onchain workflows, extend conversations across apps, and define flexible access and encryption.

## The power of the Sui Stack

The Messaging SDK isn’t just another messaging library. It interacts with three core layers of the Sui Stack to unlock communication as a programmable primitive:

* **Sui** provides verifiable identity and object-centric state, ensuring messages are first-class components of application logic.

* **Walrus** delivers decentralized, content-addressed storage for attachments, secured with proof of availability.

* **Seal** enforces programmable access control, making policies like token-gated chats, time-locked threads, or role-based groups simple to define.

Together, these layers transform messaging from a side-channel into infrastructure. Instead of bolted-on chat tools, developers can weave secure, wallet-linked communication directly into application flows, with guarantees of privacy and persistence that centralized systems cannot match.

## What you can build today

With the Sui Stack Messaging SDK in alpha, developers can already begin experimenting with messaging features that would have required heavy custom integrations in the past. 

With just a few lines of code, you can now enable:

* Direct one-to-one conversations between users, encrypted end-to-end with Seal.
* Trusted groups for customer support, community discussions, or DAO coordination.
* Message storage on Sui, encrypted with Seal and verifiable onchain.
* Attachment storage on Walrus, encrypted with Seal with defined access policies.
* Event-driven messaging that plugs directly into application flows, enabling private threads triggered by transactions, NFT mints, or governance votes.

These capabilities showcase how communication becomes part of the programmable fabric of Web3.

## Unlocking new possibilities with the Messaging SDK

The Messaging SDK makes possible a wide range of unique scenarios for builders and users alike. By treating communication as programmable infrastructure, it enables use cases that extend well beyond simple chat features.

Consider a few examples:

* **Customer support**: Deliver in-app support without pushing users to external platforms. Chats are wallet-linked, encrypted, and recoverable across devices, building trust and continuity.
* **Cross-app workflows**: Imagine a user buying an NFT in one marketplace and automatically opening a private, secure chat with a DeFi protocol about collateral options, all within a seamless, secure thread.
* **AI agent coordination**: Messaging can serve as a secure channel for agent-to-agent or app-to-agent communication, where an AI assistant can interact with a user or another AI agent, with encryption and access control guaranteed by Seal.

And these are just the start. The same framework also can support token-gated community discussions, recoverable conversations that sync across devices without centralized servers, and event-driven communication triggered by onchain activity — whether that’s a trade confirmation, a governance vote, or a content unlock.

## Getting started

The Sui Stack Messaging SDK is available now in alpha. Developers can explore the [SDK on Github](https://github.com/MystenLabs/sui-stack-messaging-sdk?ref=blog.sui.io), begin integrating messaging features into their apps, and [join the community](https://discord.com/channels/916379725201563759/1417696942074630194?ref=blog.sui.io) for feedback and roadmap discussions.

This is just the beginning. Upcoming releases will bring expanded group messaging, richer media support, and tighter integration with the broader Sui and Walrus ecosystems. 

Build with the Sui Stack Messaging SDK, and bring private, programmable communication into Web3.
