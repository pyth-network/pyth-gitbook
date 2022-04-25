# Client Libraries

We recommend using one of the following client libraries to consume Pyth prices in an application:&#x20;

* [pyth-client-rs](https://github.com/pyth-network/pyth-client-rs) ([crate](https://crates.io/crates/pyth-client)) --  Rust library for on-chain Solana programs or off-chain applications.
* [pyth-client-js](https://github.com/pyth-network/pyth-client-js) ([npm](https://www.npmjs.com/package/@pythnetwork/client)) -- Typescript/Javascript library for off-chain applications, such as displaying the Pyth price on a website.
* [pyth-client-py](https://github.com/pyth-network/pyth-client-py) ([pypi](https://pypi.org/project/pythclient/)) -- Python client for off-chain applications, such as displaying the Pyth price on a website.
* [pyth-client-go](https://github.com/Blockdaemon/pyth-go) -- Golang client for off-chain applications, such as displaying the Pyth price on a website.
* [pyth-neon](https://github.com/pyth-network/pyth-neon) -- Neon EVM compatibility layer for Ethereum applications running on Solana. This library provides a drop-in oracle replacement for Ethereum applications migrating to Solana, as it implements the same interface as most popular Ethereum oracles.

We also recommend reading the [Account Structure](../how-pyth-works/account-structure.md) document in order to understand the Solana accounts used by Pyth. This information will help you identify the accounts that contain the price information you want. A complete list of Pyth accounts can be found [here](https://pyth.network/developers/accounts/).

If you are developing a Solana program, please see the [Best Practices](best-practices.md) section for some more specific suggestions on how to best use the Pyth price and confidence interval.&#x20;
