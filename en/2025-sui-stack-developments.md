[2025 in Review: How The Sui Stack Came Together](https://blog.sui.io/2025-sui-stack-developments/)

## Main Takeaways

* *Mysticeti v2, Sui’s consensus engine, brought fast, sub-second finality to transactions across the Sui network.*
* *Walrus (decentralized storage), Seal (access control), and Nautilus (offchain data indexing) launched on mainnet in 2025, completing the core layers of the Stack.*
* *The Sui Stack is already being used to close the gap between what decentralized applications promise and what they can actually deliver.*

## Overview

While there were a number of major launches in 2025, the defining theme of the year was the assembly of a complete, decentralized development stack: **the Sui Stack**. 

With the mainnet launch of Walrus (decentralized storage), Seal (onchain access control), and Nautilus (offchain data and computation) — alongside continued improvements to Sui itself — the Sui Stack moved from a set of ideas into a usable, end-to-end system. 

Together, these layers give builders execution, storage, access control, and data indexing designed to work as one, forming the foundation for next-gen decentralized applications.

This article is part of Sui’s 2025 End of Year series, which reflects on the year from different perspectives. Here, the focus is on how the Sui Stack came together over the course of the year, and why that matters for what’s being built next.

## Sui: Faster Finality, Stronger Foundations

At the core of the Sui Stack is the Sui network itself, serving as the coordination and execution layer. Over the past year, improvements at this layer focused on making transaction processing faster, more predictable, and more resilient under real-world load.

A major step forward in execution speed and efficiency came with the release of [Mysticeti v2](https://blog.sui.io/mysticeti-v2-sui-consensus/), Sui’s consensus engine responsible for ordering and finalizing transactions across the network. As a result, transactions on Sui now finalize in well under a second for most use cases, even as activity scales.

Importantly, these gains apply broadly across the network, rather than being limited to a narrow subset of transactions as in earlier versions of Mysticeti. For builders, this means fewer tradeoffs between performance and decentralization. Applications can rely on fast execution, no matter what kinds of [objects](https://docs.sui.io/guides/developer/objects/object-model?ref=blog.sui.io) the transactions interact with.

## Walrus: Verifiable Data at Scale

[Walrus](https://www.walrus.xyz/?ref=blog.sui.io) launched on mainnet in 2025, adding a new foundational layer to the Sui Stack: decentralized storage built for scale, integrity, and programmability. 

Instead of treating data as something external to Web3 apps, Walrus makes large-scale data a native, verifiable resource that apps can depend on. It also sets the stage for data markets and AI applications that depend on high-integrity data.

Data stored on Walrus is content-addressed, versioned, and cryptographically verifiable, with tamper-evident history. That means apps can reference, reason about, and build on data directly, rather than relying on offchain services or trusted intermediaries.

As a result, Walrus unlocks new categories of decentralized applications built around verifiable data, from media and AI workloads to durable applications like decentralized archives or long-term public records where availability and integrity matter.

One of the simplest ways to see those capabilities in practice is through [Walrus Sites](https://walrus.site/?ref=blog.sui.io). Walrus Sites, decentralized websites powered by Walrus, serve both as a developer tool and a concrete example of what Walrus enables. Built using the same primitives available to the ecosystem, they provide a model for hosting decentralized frontends without relying on centralized hosting infrastructure, demonstrating how applications can move closer to truly end-to-end decentralization.

## Seal: Onchain Access Control Becomes Practical

[Seal](https://seal.mystenlabs.com/?ref=blog.sui.io) brought programmable access control to the stack.

With Seal, builders can define who can access data, under what conditions, and for how long, with enforcement tied directly to onchain access policies. Instead of managing permissions offchain, or through application-specific logic, access rules became composable and verifiable all through a native piece of the Sui Stack.

This capability becomes especially important as applications grow more expressive onchain, building on the capabilities introduced by Sui and Walrus. As data, identity, and content become more central to onchain applications, Seal provides a way to manage permissions natively without sacrificing decentralization.

## Nautilus: Making Offchain Data Usable

As applications become more sophisticated, they need more than just raw onchain data. They also need ways to safely incorporate external information and handle work that doesn’t belong directly onchain.

[Nautilus](https://sui.io/nautilus?ref=blog.sui.io) provides this layer for the Sui Stack by enabling hybrid applications to work with data that originates outside of Sui, while still grounding it in verifiable logic and history. This includes external inputs and computed data that applications can trust without pushing complexity or cost onto the chain itself.

In practice, this means applications can use Nautilus to bring in information from other networks, perform computationally intensive tasks offchain, or work with sensitive data that should not be publicly exposed. 

Rather than relying on centralized services or custom pipelines, Nautilus offers a decentralized way to make this data available to applications built on Sui.

By connecting onchain execution with trusted external and offchain data, Nautilus fills a critical foundational layer of the Sui Stack. It closes the gap between what decentralized applications promise and what they can actually deliver in practice.

## A Working Example: The Messaging SDK

With the core layers of the Sui Stack in place, new primitives become possible. One of the clearest examples is messaging, which has traditionally depended on centralized services. The [Sui Stack Messaging SDK](https://blog.sui.io/sui-stack-messaging-sdk/) shows what becomes possible when execution, storage, and access control are designed to work together from the start.

The Messaging SDK is built directly on the Sui Stack, combining execution on Sui, durable storage through Walrus, and programmable access control via Seal. It gives builders a native way to send structured messages to wallets and applications based on onchain state and object interactions, enabling applications to communicate directly with users as they interact with assets, approvals, and app-specific workflows.

As a result, applications can notify users at the right moments without relying on centralized messaging infrastructure. Messages can be created and verified onchain, stored securely, and shared according to explicit permission rules, turning a common offchain dependency into a reusable, composable primitive.

The Messaging SDK highlights how combining execution, storage, and access control unlocks capabilities that aren’t possible when these layers are built in isolation.

## Ready for What Comes Next

Over the course of 2025, the Sui Stack moved from a clear vision into a tangible, working system. Execution, storage, access control, and data indexing are no longer separate concerns stitched together, but coordinated layers of a single stack. 

With these foundations in place, builders can spend less time assembling core plumbing and more time shaping applications that are fully onchain, verifiable by design, and built to scale reliably from day one. Just as importantly, teams across the ecosystem are already building with these components and putting them into practice.

As the Sui Stack continues to mature, ongoing improvements will expand what’s possible even further, but the core pieces are now in place. What comes next will be shaped by how the community chooses to build on top of them.
