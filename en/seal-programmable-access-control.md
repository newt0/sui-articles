[Seal: Programmable Access Control for Real-World Apps](https://blog.sui.io/seal-programmable-access-control/)

## Seal: Programmable Access Control for Real-World Apps

Seal lets products enforce access where it matters most: at the data boundary.

* [![Sui Foundation](https://blog.sui.io/content/images/size/w100/2023/04/Sui_Droplet_Logo_Blue-3.png)](https://blog.sui.io/author/sui-foundation/)

![Seal: Programmable Access Control for Real-World Apps](https://blog.sui.io/content/images/size/w2000/2025/11/3_Blog-Header_Seal-Access-Control--1-.png)

Most access systems weren’t built for how products actually work. Traditional Web2 Cloud Identity and Access Managements (IAM) tools are designed around infrastructure, controlling who can call which API, instead of focusing on products and users where access depends on data, context, and timing. 

To fill that gap, teams often bolt on Role-Based Access Control ([RBAC](https://en.wikipedia.org/wiki/Role-based_access_control?ref=blog.sui.io)) or Attribute-Based Access Control ([ABAC](https://en.wikipedia.org/wiki/Attribute-based_access_control?ref=blog.sui.io)) layers using third-party products or custom layers, which makes the architecture more complex and fragile.

[**Seal**](https://seal.mystenlabs.com/?ref=blog.sui.io) **takes a different approach**: it makes encryption the gate and policy the key. Data stays encrypted by default and only decrypts when a programmable access policy explicitly allows it. Because rules live with the data itself, you can express app-level rules cleanly, including different rules for different parts of the same app, without stitching together multiple external systems.

## Why programmable access beats bolt-on IAM

Cloud IAM solves infrastructure questions like “can this principal identity call this endpoint?” Most products, however, need business-level rules: who may open this object, under these conditions, at this moment. With Seal, you write that logic as policy code that travels with the data. The ciphertext can move across services, clouds, or storage backends, yet it only decrypts when the policy approves, **enabling selective disclosure by default**.

This model reduces sprawl. Instead of duplicating roles, scopes, and permission lists across gateways, microservices, and databases, you encode the rule once at the data boundary. Because the policy state is anchored on [Sui](https://sui.io/?ref=blog.sui.io) and with optional storage of access logs on [Walrus](https://walrus.xyz/?ref=blog.sui.io), you get a durable, auditable trail that’s clearer than scattered server logs. The result is simpler operations, fewer places where secrets can leak, and policies that map directly to features, including subscriptions, embargoes, licensing terms, rather than to network or API plumbing.

## Policies you can actually use

Seal ships with [reusable patterns](https://seal-docs.wal.app/ExamplePatterns/?ref=blog.sui.io) you can mix and match inside one product. The following examples illustrate how you could encode these rules in Sui smart contracts:

* **Allowlist or membership** - Share encrypted content with a defined group of users or AI agents. 
  * Sui policy example: “Members of Gold tier can open documents tagged \*gold/\*\*.”
* **Time-locked access** - Coordinate reveals for asset drops or auctions. 
  * Sui policy example: “Decrypt after *2025-11-01T00:00Z* unless a legal hold is active.”
* **Subscriptions & licensing** - Time-bound, paid access to premium content or API results.
  * Sui policy example: “Active subscription AND region = EU AND license scope includes *model.infer*.”
* **Owner-private data** - Portable encrypted objects that only the current owner can open.
  * Sui policy example: “Only the current NFT holder can decrypt attached perks.”
* **Secure voting or tallies** – Keep ballots encrypted until conditions are met, then produce a verifiable tally on-chain. 
  * Sui policy example: “Decrypt results when quorum ≥ 60% and voting window is closed.”
* **Pre-signed-style windows** - Time-limited, bearer-style access to specific Walrus blobs.
  * Sui policy example: “Allow decryption for this blob until *link.expiry*.”

### Real-world examples

These policy patterns can be used across a wide range of verticals:

* **Enterprise data rooms** - “If counterparty has signed NDA AND deal phase ≥ *DD,* unlock the dataset at \*/dataroom/acme/\*\*; Regulators see audit logs only.”
* **AI & data licensing** - “If client holds *dataset.read* for SKU X, allow inference with model Y from 09:00-17:00 UTC; Deny export of raw training data.”
* **Media & creator platforms** - “Subscribers can stream videos for 30 days; Non-subscribers can decrypt 30-sec previews.”
* **Digital marketing** - “Campaign analysts can decrypt aggregated cohort metrics by default; Individual-level data stays sealed unless a valid user-consent token is present and is unexpired.”
* **Fintech** - “Auditor role decrypts redacted data for reported cases during review window; PII fields stay hidden until risk mgmt approval is attached.”

You can apply different policies to different features in the same app, like membership-gated content, time-locked previews, and per-user private notes, all without a tangle of ad-hoc access control lists.

## Why this is simpler than traditional IAM

Most teams start with cloud IAM for APIs, integrate with an identity provider, optionally add a third-party system for RBAC, and then roll their own rule engine to reflect product logic. Each layer speaks a different language (roles, scopes, conditions), and none is attached to the data itself. You end up duplicating rules, leaking secrets between microservices, and relying on logs to prove who could access what.

With Seal, the enforcement point is the data boundary. Data is encrypted until a policy says otherwise; policies are code you control and audit; and approvals can be recorded on Walrus. You stop scattering authorization across gateways, services, and storage systems. Instead of maintaining three overlapping control planes, you encode business rules once, next to your product logic, and let encryption do the heavy lifting. That reduces moving parts, shrinks the blast radius of mistakes, and gives stakeholders a clear rule: “if the policy didn’t approve, the data never decrypted.”

## How it works in practice

At a high level, you encrypt data with Seal so plaintext isn’t exposed by default, and then capture your business rules as a small, auditable policy program. Decryption requires threshold approval from independent key servers (and, soon, multi-party computation committees) that evaluate the policy, and only on success does a client or permitted backend receive the keys to decrypt the data.

Developers can implement this quickly using the SDK and easy-to-adapt Sui-based policy patterns, using Seal in new apps along with Walrus and optionally [Nautilus](https://sui.io/nautilus?ref=blog.sui.io), or fitting in existing architectures and replacing scattered authorization glue with concise, verifiable policy code.

## Try it out

Pick one sensitive flow, that includes premium content, dataset, or message attachment, and protect it with Seal behind a simple policy (membership or time lock is a good first step). Store the ciphertext where you already keep content, like Walrus. As you gain confidence, extend the approach to subscriptions, licensing, and per-feature rules, applying different policies to different parts of the product in an incremental fashion. Take a look at the [getting started guide](https://seal-docs.wal.app/GettingStarted/?ref=blog.sui.io).

Seal puts business-level access where it belongs, at the data, so you can build products that are private by default, easy to reason about, and ready for real-world obligations.
