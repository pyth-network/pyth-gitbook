---
description: Consume Pyth Network prices in applications on Cosmwasm
---

# Pyth on Cosmwasm

Cosmwasm contracts can update and fetch the Pyth prices using the Pyth Cosmwasm Contract, which has been deployed on Testnet. The documented source code can be found [here](https://github.com/pyth-network/pyth-crosschain/tree/main/target-chains/cosmwasm/contracts/pyth).

## Updating Price Feeds

The mechanism by which price feeds are updated on Cosmwasm is explained [here](./pythnet-price-feeds.md). Once fetched, price feed update data can be passed to the `ExecuteMsg`, on-chain function.

## Examples
- [Minimal on-chain contract](https://github.com/pyth-network/pyth-crosschain/blob/main/target-chains/cosmwasm/examples/cw-contract) which queries the pyth contract. 

## Networks

Pyth is currently available on the following cosmwasm chains: 
### Testnet
| Network   | Contract address                             |
| --------- | -------------------------------------------- |
| Injective | `inj1z60tg0tekdzcasenhuuwq3htjcd5slmgf7gpez` |

## Price Feeds

| Network | Available Price Feeds                                             |
| -------------- | -----------------------------------------------------------|
| Injective Testnet  |[https://pyth.network/developers/price-feed-ids#injective-testnet](https://pyth.network/developers/price-feed-ids#injective-testnet)|