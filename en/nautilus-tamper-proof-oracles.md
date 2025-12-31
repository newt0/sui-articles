[Build Tamper-Proof Oracles with Nautilus on Sui Mainnet](https://blog.sui.io/nautilus-tamper-proof-oracles/)

## Build Tamper-Proof Oracles with Nautilus on Sui Mainnet

Nautilus is now live on Sui Mainnet, bringing tamper-proof, verifiable offchain computation to Web3 apps.

* [![Sui Foundation](https://blog.sui.io/content/images/size/w100/2023/04/Sui_Droplet_Logo_Blue-3.png)](https://blog.sui.io/author/sui-foundation/)

![Build Tamper-Proof Oracles with Nautilus on Sui Mainnet](https://blog.sui.io/content/images/size/w2000/2025/06/27-05-2-Blog-Header.png)

[Nautilus](http://sui.io/nautilus?ref=blog.sui.io), a crucial piece of Web3 infrastructure, is now live on Sui Mainnet. With Nautilus, developers can offload their app-specific offchain computation to tamper-proof Trusted Execution Environments (TEEs), enabling the flexibility of offchain logic while preserving the cryptographic trust guarantees of onchain execution.

Most current offchain computation remains opaque and unverifiable. Oracles, used to bring external data like weather or price feeds onchain, are a prime example. These systems typically rely on closed-source infrastructure, and users must trust that the data is being processed and delivered as claimed.

With Nautilus, developers can create oracles and offchain flows that are tamper-proof and verifiable onchain. Any app that needs to process sensitive data, heavy computations, or real-world inputs can now do so without compromising on trust.

## Offchain computation is a trust bottleneck

Oracles are a critical part of Web3 infrastructure, acting as connective tissue between blockchains and the real world. They allow smart contracts to respond to offchain events, from asset prices and weather conditions to sports scores and social activity. But under the hood, nearly all of them rely on offchain computation—code running outside the network’s security model.

That’s where the problem begins. Offchain systems are difficult to verify and easy to manipulate. Users are often left to trust whatever server, script, or third-party provider processed the data, with no way to inspect or audit what actually happened.

In most cases offchain infrastructure involves:

* Centralized servers that can be modified, misconfigured, or compromised.
* Bots parsing APIs or scraping data with no verifiable integrity or audit trail.
* "Trust me" signatures from Web2 services that provide no proof of how the data was collected or processed.

Even decentralized oracle networks often fall short, introducing added latency and complexity, without fully solving the verifiability problem. For Web3 to scale into more serious, data-driven use cases, offchain logic needs to be as trustworthy as the blockchain it supports.

## Nautilus: A new approach to verifiable offchain logic

[Nautilus](http://sui.io/nautilus?ref=blog.sui.io) was built to address this challenge head-on. It enables secure offchain computation in Web3 using TEEs (starting with [AWS Nitro Enclaves](https://aws.amazon.com/ec2/nitro/nitro-enclaves/?ref=blog.sui.io)) and verifies the results directly onchain via smart contracts.

Each Nautilus enclave runs a specific piece of code that, if a service provider chooses to, is publicly auditable and cryptographically measured. This means anyone can inspect the source code that’s been deployed, generate cryptographic properties of it themselves, and confirm that the enclave is running exactly what it claims to—nothing more, nothing less. Once deployed, the enclave executes that code in an isolated, tamper-proof environment, generating a signed output along with an attestation that proves its integrity.

That signed response is then submitted to Sui, where onchain Move smart contracts verify both the attestation and the response itself. If everything checks out (i.e., the enclave is registered, the code matches the expected cryptographic properties, and the signature is valid), the smart contract accepts the data and can act on it.

This flow creates a new standard for oracle and offchain design, logic that’s not only tamper-proof and isolated, but provably transparent and verifiable from end to end.

## Building a secure oracle with Nautilus

With Nautilus, developers can create oracles that prove exactly how offchain data was handled. Here’s how to build one step by step:

1. **Write your data-fetching logic.**

Start by defining the logic your oracle needs—whether it’s fetching an exchange rate, reading a weather API, or validating a Twitter post. This code will run inside a secure enclave.

2. **Deploy the logic to a Nitro Enclave.**

Use the Nautilus framework to compile and launch your code in an AWS Nitro Enclave. The enclave provides a tamper-proof runtime that ensures your logic executes securely and in isolation.

3. **Register your enclave on-chain.**

Once deployed, register your enclave’s attestation data, such as [PCR values](https://docs.aws.amazon.com/enclaves/latest/user/set-up-attestation.html?ref=blog.sui.io) and public key, on Sui using a Move smart contract. This allows the chain to later verify that responses came from a known, trusted enclave.

4. **Fetch and sign external data.**

The enclave can now fetch offchain data, process it according to your logic, and sign the output along with its attestation.

5. **Submit the result to Sui.**

Send the signed result onchain, where a Move contract verifies that it came from a valid, registered enclave. If verified, the smart contract can take action, such as updating a price, minting a token, or triggering a payout.

With this foundation in place, developers can adapt the pattern to fit a wide variety of use cases. Examples include:

* **Price feeds** that fetch exchange rates from a web API and update AMMs (Automated Market Makers).
* **Reputation or scoring systems** for prediction markets or social platforms that calculate rankings privately, then commit results publicly.
* **Geolocation or weather-based NFTs**, where the oracle verifies external conditions before minting rewards.
* **Trust-minimized social-linked flows**, that verify a user’s tweet or Venmo payment before triggering on-chain asset transfers.

## Now live on Sui Mainnet

With Nautilus now live on Sui Mainnet, developers can finally build offchain systems, like oracles, that are verifiable by default, and without sacrificing performance, flexibility, or user trust. Whether you’re integrating external data, handling sensitive computations, or building entirely new types of apps, Nautilus provides the tools to make it tamper-proof and onchain-verifiable.

This isn’t a new oracle framework, it’s a new model for connecting Web3 to the real world with integrity baked in. 

Get started building today by referring to the [Nautilus documentation](https://docs.sui.io/concepts/cryptography/nautilus?ref=blog.sui.io) and [sample app](https://github.com/MystenLabs/nautilus-twitter?ref=blog.sui.io).

Have questions or want to jam with other builders? Join the conversation on [Discord](https://discord.com/channels/916379725201563759/1361500579603546223?ref=blog.sui.io).
