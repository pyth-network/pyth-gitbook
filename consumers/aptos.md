---
description: Consume Pyth Network prices in applications on Aptos
---

# Pyth on Aptos

Aptos contracts can update and fetch the Pyth prices using the Pyth Aptos Contract, which has been deployed on Testnet. The documented source code can be found [here](https://github.com/pyth-network/pyth-crosschain/blob/main/aptos/contracts/sources/pyth.move).

## Updating Price Feeds

The mechanism by which price feeds are updated on Aptos is explained [here](./consume-data.md). The [pyth-aptos-js](https://github.com/pyth-network/pyth-js/tree/main/pyth-aptos-js) package can be used to fetch price feed update data which can be passed to the `pyth::update_price` on-chain function.

## Examples
- [Minimal on-chain contract](https://github.com/pyth-network/pyth-crosschain/blob/main/aptos/examples/fetch_btc_price) which updates and returns the Pyth BTC/USD price.
- [Full-stack React app and on-chain contract](https://github.com/pyth-network/pyth-crosschain/blob/main/aptos/examples/mint_nft) which uses the [pyth-aptos-js](https://github.com/pyth-network/pyth-js/tree/main/pyth-aptos-js) package to update the price used by the contract.

## Networks 

Pyth is currently deployed on Aptos Testnet, and will be available on Aptos Mainnet as soon as the chain is live.

## Addresses

When deploying contracts using Pyth, the [named addresses](https://diem.github.io/move/address.html#named-addresses) `pyth`, `wormhole` and `deployer` need to be defined at compile time. These addresses are the same across both Testnet and Mainnet.

| Named Address | Value                                                               |
| ------------- | --------------------------------------------------------------------|
| `pyth`        | `0xa1c1e6ec8eca84d93d0c0d2708b840c16895389e6e55c31a6447c97c9257d069`|
| `wormhole`    | `0x5bc11445584a763c1fa7ed39081f1b920954da14e04b32440cba863d03e19625`|
| `deployer`    | `0xb31e712b26fd295357355f6845e77c888298636609e93bc9b05f0f604049f434`|

`deployer` and `wormhole` are implementation details of the Pyth contract: you will not need to interact with these.

## Price Feeds

| Network | Available Price Feeds                                             |
| -------------- | -----------------------------------------------------------|
| Aptos Testnet  |https://pyth.network/developers/price-feed-ids#aptos-testnet|
| Aptos Mainnet  |https://pyth.network/developers/price-feed-ids#aptos-mainnet|
