---
description: Official IOTA Wallet Library Software which can be used to easily integrate an IOTA Wallet into your application 
image: /img/logo/wallet_light.png
keywords:
- wallet
- software
- library
- rust
- python
- nodejs
- java
- value transactions
---

# Welcome

The wallet.rs library helps developers build applications that require value transactions within the Shimmer network: exchanges, pay-as-you systems, and of course [personal wallets](https://wiki.iota.org/shimmer/use/wallets/firefly/general/). The library provides convenient ways to create, manage and back up accounts, and to track the balance and issue new transactions.

We have written wallet.rs in Rust and we provide bindings for Java, Node.js, and Python. It uses the [iota.rs](https://wiki.iota.org/shimmer/iota.rs/welcome/) library to communicate with the network.

![High-level overview of the Shimmer network.](/img/overview/iota_layers_overview.svg "Click to see the full-size image.")

*High-level overview of the Shimmer network.*

## Security

The wallet.rs library provides no security measures on its own. We assume that you store and manage the seed within a secure enclave, be it a software solution like [stronghold.rs](https://wiki.iota.org/stronghold.rs/welcome/) or a hardware ledger like Ledger Nano.

## Seeds, Accounts, and Addresses

The wallet.rs library uses an [account model](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki). Instead of deriving addresses directly from the seed, it creates one or multiple accounts and derives addresses from them. Each account has its own set of addresses, and you can assign meaningful aliases to them.

![Seed, accounts and Addresses](/img/libraries/accounts_addresses.svg)
![A scheme with a single seed. Multiple accounts derive from that seed, and multiple addresses derive from each address.](/img/libraries/accounts_addresses.svg "Click to see the full-size image.")

*A seed and the accounts and addresses that derive from it.*

If you have multiple users (for example, if you are implementing an exchange), you could assign 
an account for each individual user, or you could use a single account and assign an address to each user. The former is more flexible, the latter is commonly used at exchanges as the developers find it easier to use, implement, and backup. Both approaches are equally viable.