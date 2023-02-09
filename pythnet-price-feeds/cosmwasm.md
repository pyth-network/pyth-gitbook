---
description: Consume Pyth Network prices in applications on Cosmwasm
---

# Pyth on Cosmwasm

Cosmwasm contracts can update and fetch the Pyth prices using the Pyth Cosmwasm Contract, deployed on their network. The documented source code can be found [here](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/cosmwasm/contracts/pyth).

## Updating Price Feeds

The mechanism by which price feeds are updated on Cosmwasm is explained [here](./pythnet-price-feeds.md). The [pyth-common-js](https://github.com/pyth-network/pyth-js/tree/main/pyth-common-js) can be used to fetch the latest price feed data which then can be passed to the `ExecuteMsg`, on-chain function.

## Examples
- [Minimal on-chain contract](https://github.com/pyth-network/pyth-crosschain/blob/main/target_chains/cosmwasm/examples/cw-contract) which queries the pyth contract. 

## Networks

Pyth is currently available on the following cosmwasm chains: 
### Testnet
| Network   | Contract address                             |
| --------- | -------------------------------------------- |
| Injective | `inj1z60tg0tekdzcasenhuuwq3htjcd5slmgf7gpez` |

## Price Feeds

| Network | Available Price Feeds                                             |
| -------------- | -----------------------------------------------------------|
| Cosmwasm Testnet  |[https://pyth.network/developers/price-feed-ids#cosmwasm-testnet](https://pyth.network/developers/price-feed-ids#cosmwasm-testnet)|