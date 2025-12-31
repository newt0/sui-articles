[Exploring the Bitcoin-Backed Assets Powering BTCfi on Sui](https://blog.sui.io/bitcoin-backed-assets-powering-btcfi/)

Bitcoin has long been thought of as digital gold, but until recently, it hasn’t been programmable. Sui changes that. With the rise of BTCfi, users can now easily move BTC onto Sui and put it to work across various DeFi products. But no two Bitcoin-backed assets on Sui are created equal. Each one takes a different approach to bridging, custody, and integration, reflecting a wide spectrum of trust models and design philosophies.

Here’s a closer look at how Bitcoin is gaining utility on Sui, one asset at a time.

## wBTC: via Sui Bridge

For users already holding wBTC on Ethereum, [Sui Bridge](https://bridge.sui.io/?ref=blog.sui.io) offers a straightforward way to bring that asset onto Sui. This follows a typical custodial bridge model: wBTC on Ethereum is locked, and an equivalent amount of wBTC is minted on Sui, but with a meaningful difference. Instead of relying on a traditional multisig or external custodian, the bridge is secured by Sui’s validator set, which verifies and finalizes bridging transactions on Sui. This ties the integrity of the bridge directly to the same decentralized infrastructure that secures Sui itself. 

The result is a familiar mechanism, with stronger alignment to Sui’s security model. For users seeking a straightforward way to move wBTC from Ethereum to Sui, bridging wBTC via Sui Bridge is the best fit option.

## LBTC: BTC liquid staked on Babylon

LBTC, issued by Lombard, is part of a broader effort to make Bitcoin usable in a composable, high-performance environment. Users mint LBTC by locking BTC into a vault operated by a multisig custody system. That BTC remains fully backed and redeemable, while LBTC becomes the liquid representation of that value on Sui.

Behind the scenes, when BTC is deposited, Lombard stakes it on Babylon, meaning that while your BTC remains securely held, it also contributes to Babylon’s Bitcoin-secured Proof-of-Stake infrastructure. Because LBTC is structured as a liquid staking token, holders can access protocol-level yield distributions, earning rewards denominated in Babylon’s token, without ever giving up the use of their tokens on Sui. This model preserves full liquidity while enabling Bitcoin to work in multiple layers at once.

Lombard’s current multisig custody is a necessary foundation, but it’s just the starting point. Their long-term ambition is to shift to a decentralized vault architecture, built onchain and operated by distributed governance and automated rules. This evolution would remove the need for centralized custodians and bring LBTC to full parity with trust-minimized assets.

## xBTC: exchange-native liquidity

xBTC is issued by [OKX](https://www.okx.com/en-us?ref=blog.sui.io) and designed to bridge the gap between centralized exchange liquidity and decentralized apps on Sui. Rather than requiring users to self-custody BTC and interact with an external bridge, xBTC allows OKX account holders to seamlessly move their BTC into Sui as a wrapped token. This direct path from exchange to chain reduces complexity and opens the door to onchain activity for users who are already active in centralized markets.

While xBTC relies on custodial infrastructure, its strength lies in integration and convenience. OKX, the world's second-largest crypto exchange by volume, handles the backend custody, offering users a low-friction experience that aligns with how they already interact with digital assets. For those who prioritize efficiency and are comfortable with trusted platforms, xBTC offers a practical onramp to BTCfi on Sui without additional bridging steps.

## tBTC: built on Cryptographic Trust

tBTC brings Bitcoin onto Sui without relying on centralized bridges or custodians. Developed by the [Threshold Network](https://threshold.network/?ref=blog.sui.io), tBTC uses threshold cryptography and a decentralized network of nodes to custody BTC in a trust-minimized way. When users deposit Bitcoin, no single party controls it, instead, custody is distributed across a network that collectively signs and secures the asset through cryptographic protocols.

This architecture reflects Bitcoin’s own values of neutrality and permissionlessness. On Sui, tBTC becomes a programmable extension of BTC that preserves those principles. Holders can participate in DeFi without trusting a custodian or intermediary, and developers can integrate a Bitcoin-backed asset that aligns with the ethos of decentralization. For users who want to bring BTC into DeFi while minimizing reliance on trusted third parties, tBTC offers one of the most resilient paths available.

## sBTC: directly integrated with Bitcoin logic

Unlike other BTCfi assets on Sui, sBTC is not issued through a traditional lock-and-mint bridging process. Instead, it originates from [Stacks](https://www.stacks.co/?ref=blog.sui.io), an independent protocol that connect to Bitcoin through a consensus mechanism called [Proof of Transfer](https://www.stacks.co/faq/what-is-proof-of-transfer?ref=blog.sui.io). This setup allows sBTC to inherit Bitcoin’s security guarantees while enabling smart contract functionality.

When sBTC appears on Sui, it does so as part of a cross-ecosystem collaboration rather than a direct lock-and-mint process. While the custody and minting mechanics differ from other wrapped BTC assets, sBTC offers a unique avenue for developers and users who want to bridge functionality across multiple Bitcoin-aligned networks. It’s less about wrapping BTC, and more about extending its reach.

## Quick comparison of BTCfi assets on Sui

Each of these assets brings Bitcoin onto Sui through a different lens, shaped by unique custody models, trust assumptions, and integration paths. Here’s a snapshot of how they compare:

|
Asset

|

Origin

|

Custody Model

|

Key Feature

|  |
|  |

|

wBTC

|

Sui Bridge

|

Custodial (relies on custody of the wBTC contract on Ethereum)

|

Native Ethereum wBTC bridged to Sui

|
|

LBTC

|

Lombard

|

Multisig (evolving to decentralized vaults)

|

Liquid staked BTC that earns protocol rewards via Babylon

|
|

xBTC

|

OKX

|

Custodial (exchange-held)

|

Exchange-native minting and redemption

|
|

tBTC

|

Threshold Network

|

Distributed threshold cryptography

|

Trustless custody with no single point of control

|
|

sBTC

|

Stacks Protocol

|

Secured via Bitcoin Proof of Transfer

|

Smart contract functionality rooted in the Bitcoin network

|

## BTC comes alive on Sui

Bitcoin’s role in Web3 is evolving from static store of value to dynamic, programmable asset. On Sui, that evolution is happening through a growing set of BTC-backed assets, each with its own trade-offs, trust assumptions, and integration paths. Whether you’re optimizing for decentralization, speed, composability, or ease of access, there’s a BTCfi option that fits your priorities. And as the ecosystem matures, these assets aren’t just bringing Bitcoin to Sui, they’re bringing it to life.

*Note: This content is for general educational and informational purposes only and should not be construed or relied upon as an endorsement or recommendation to buy, sell, or hold any asset, investment or financial product and does not constitute financial, legal, or tax advice.*
