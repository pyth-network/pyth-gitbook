# Off-Chain Applications

We provide SDKs in various programming languages that allow you to read the values of Pyth price feeds in off-chain applications, such as web frontends:

{% tabs %}
{% tab title="JavaScript" %}
There are different javascript SDKs for different purposes.

If you are developing an application that runs on any blockchain except Solana, then the [javascript SDK for that blockchain](https://github.com/pyth-network/pyth-js) supports querying and streaming live Pyth prices.
These SDKs also support generating [on-demand price updates](on-demand.md) for your target blockchain.
An example for querying and streaming prices using these SDKs is shown [here](https://github.com/pyth-network/pyth-js/tree/main/pyth-evm-js#off-chain-prices).

If you are developing an application for Solana, or without any blockchain whatsoever, then the [@pythnetwork/client](https://www.npmjs.com/package/@pythnetwork/client) npm package can be used to consume Pyth prices inside off-chain JavaScript programs.
An example can be found [here](https://github.com/pyth-network/pyth-client-js#example-usage).
{% endtab %}

{% tab title="Rust" %}
The [pyth-sdk-solana crate](https://crates.io/crates/pyth-sdk-solana) can be used to consume Pyth prices inside your off-chain Rust programs. An example can be found [here](https://github.com/pyth-network/pyth-sdk-rs/blob/main/pyth-sdk-solana/examples/eth\_price.rs).
{% endtab %}

{% tab title="Python" %}
The [pyth-client-py](https://github.com/pyth-network/pyth-client-py) Python library can be used to consume Pyth prices inside your off-chain Python programs. An example can be found [here](https://github.com/pyth-network/pyth-client-py/blob/main/examples/read\_one\_price\_feed.py).
{% endtab %}

{% tab title="Go" %}
The [Blockdaemon pyth-go](https://github.com/Blockdaemon/pyth-go) client can be used to consume Pyth prices inside your off-chain Go programs.
{% endtab %}
{% endtabs %}

