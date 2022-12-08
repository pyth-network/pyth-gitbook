---
description: Consume Pyth prices in Solana programs.
---

# Pyth on Solana

We provide two different SDKs for Solana on-chain programs to use Pyth prices:

{% tabs %}
{% tab title="Rust" %}
The [pyth-sdk-solana crate](https://github.com/pyth-network/pyth-sdk-rs/tree/main/pyth-sdk-solana) can be used to consume Pyth prices inside Solana programs written in Rust.
{% endtab %}

{% tab title="NEON EVM" %}
[NEON](https://neon-labs.org) is an EVM compatibility layer for Solana, allowing users to migrate their Ethereum applications to Solana with minimum effort.

The [pyth-neon](https://github.com/pyth-network/pyth-neon) library is an interface to Pyth oracles for NEON applications.
{% endtab %}
{% endtabs %}

## Example Program

The Pyth Solana SDK includes two example programs that demonstrate how to use Pyth price feeds in Solana programs:
a [program using only the basic Solana SDK](https://github.com/pyth-network/pyth-sdk-rs/tree/main/examples/sol-contract) and an [Anchor program](https://github.com/pyth-network/pyth-sdk-rs/tree/main/examples/sol-anchor-contract).

## Price Feed IDs

The price feeds available on each Solana network are listed on the following pages:

- [Devnet](https://pyth.network/developers/price-feed-ids#solana-devnet)
- [Testnet](https://pyth.network/developers/price-feed-ids#solana-testnet)
- [Mainnet-Beta](https://pyth.network/developers/price-feed-ids#solana-mainnet-beta)
