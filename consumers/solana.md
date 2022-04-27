---
description: Consume prices from Pyth on Solana in your on- and off-chain programs.
---

# Pyth on Solana

{% hint style="info" %}
We recommend reading the [Solana Account Structure](another-page.md) documentation when using Pyth on Solana.
{% endhint %}

## On-Chain Programs

{% tabs %}
{% tab title="Solana" %}
The [pyth-sdk-solana crate](https://github.com/pyth-network/pyth-sdk-rs/tree/main/pyth-sdk-solana) can be used to consume Pyth prices inside your Solana programs.
{% endtab %}

{% tab title="NEON EVM" %}
[NEON](https://neon-labs.org) is an EVM compatibility layer for Solana, allowing users to migrate their Ethereum applications to Solana with minimum effort.

The [pyth-neon](https://github.com/pyth-network/pyth-neon) library provides a drop-in replacement for the most popular Ethereum oracle, which Ethereum apps migrating to Solana can use.
{% endtab %}
{% endtabs %}

## Off-Chain Clients

{% tabs %}
{% tab title="JavaScript" %}
The [@pythnetwork/client](https://www.npmjs.com/package/@pythnetwork/client) npm package can be used to consume Pyth prices inside your off-chain JavaScript programs. An example can be found [here](https://github.com/pyth-network/pyth-client-js#example-usage).
{% endtab %}

{% tab title="Rust" %}
The [pyth-sdk-solana crate](https://crates.io/crates/pyth-sdk-solana) can be used to consume Pyth prices inside your off-chain Rust programs. An example can be found [here](https://github.com/pyth-network/pyth-sdk-rs/blob/main/pyth-sdk-solana/examples/eth\_price.rs).
{% endtab %}

{% tab title="Python" %}
The [pyth-client-py](https://github.com/pyth-network/pyth-client-py) Python library to consume Pyth prices inside your off-chain Python programs. An example can be found [here](https://github.com/pyth-network/pyth-client-py/blob/main/examples/read\_one\_price\_feed.py).
{% endtab %}

{% tab title="Go" %}
The [Blockdaemon pyth-go](https://github.com/Blockdaemon/pyth-go) client can be used to consume Pyth prices inside your off-chain Go programs.
{% endtab %}
{% endtabs %}
