---
description: Consume Pyth prices in Solana programs.
---

# Pyth on Solana

We provide two different SDKs for Solana on-chain programs to use Pyth prices:

{% tabs %}
{% tab title="Solana" %}
The [pyth-sdk-solana crate](https://github.com/pyth-network/pyth-sdk-rs/tree/main/pyth-sdk-solana) can be used to consume Pyth prices inside your Solana programs.
{% endtab %}

{% tab title="NEON EVM" %}
[NEON](https://neon-labs.org) is an EVM compatibility layer for Solana, allowing users to migrate their Ethereum applications to Solana with minimum effort.

The [pyth-neon](https://github.com/pyth-network/pyth-neon) library is an interface to Pyth oracles for NEON applications.
{% endtab %}
{% endtabs %}

Pyth continuously updates its price feeds on Solana, so users do not have to relay Wormhole messages on-chain.

## Example

The Pyth Solana SDK includes a full [example on-chain contract](https://github.com/pyth-network/pyth-sdk-rs/tree/main/examples/sol-contract) that shows how to use Pyth price feeds.

## Price Feed IDs

The price feeds available on each Solana network are listed on the following pages:

- [Devnet](https://pyth.network/developers/price-feed-ids#solana-devnet)
- [Testnet](https://pyth.network/developers/price-feed-ids#solana-testnet)
- [Mainnet-Beta](https://pyth.network/developers/price-feed-ids#solana-mainnet-beta)
