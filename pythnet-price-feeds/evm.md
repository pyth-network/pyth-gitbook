---
description: Consume Pyth Network prices in EVM applications
---

# Pyth on EVM

On-chain EVM programs can use the [Solidity SDK](https://github.com/pyth-network/pyth-sdk-solidity) to read Pyth prices. The off-chain portion of the application can use [pyth-evm-js](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/ethereum/sdk/js) to generate price update transactions. This repository's [Quickstart](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/ethereum/sdk/js#quickstart) includes an example of both the on- and off-chain code necessary to integrate with Pyth.

## EVM price pusher

[Pyth EVM price pusher](https://github.com/pyth-network/pyth-crosschain/tree/main/price_pusher)
is a service that regularly pushes price updates to the on-chain Pyth contract.
Protocols can run this service to push regular updates to the on-chain Pyth price based on various conditions, such as a minimum update frequency, or a price change threshold.
This service is useful for protocols that already depend on regular push updates and want to simplify  migrating to Pyth.
Please see the github readme for additional information on this service.

## Networks

Pyth is currently available on the following EVM-based chains:

### Mainnet

| Network   | Contract address                             |
| --------- | -------------------------------------------- |
| Avalanche | `0x4305FB66699C3B2702D4d05CF36551390A4c69C6` |
| Fantom    | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Polygon   | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| BNB       | `0x4D7E825f80bDf85e913E0DD2A2D54927e9dE1594` |
| Ethereum  | `0x4305FB66699C3B2702D4d05CF36551390A4c69C6` |
| Optimism  | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Aurora    | `0xF89C7b475821EC3fDC2dC8099032c05c6c0c9AB9` |
| Arbitrum  | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Celo      | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| KCC       | `0xE0d0e68297772Dd5a1f1D99897c581E2082dbA5B` |
| Cronos    | `0xE0d0e68297772Dd5a1f1D99897c581E2082dbA5B` |
| ZkSync    | `0xf087c864AEccFb6A2Bf1Af6A0382B0d0f6c5D834` |
| EVMOS     | `0x354bF866A4B006C9AF9d9e06d9364217A8616E12` |


### Testnet

| Network                    | Contract address                             |
| -------------------------- | -------------------------------------------- |
| Goerli (Ethereum testnet)  | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Fuji (Avalanche testnet)   | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Fantom testnet             | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Mumbai (Polygon testnet)   | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| BNB testnet                | `0xd7308b14BF4008e7C7196eC35610B1427C5702EA` |
| Aurora testnet             | `0x4305FB66699C3B2702D4d05CF36551390A4c69C6` |
| Optimism Goerli (testnet)  | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Celo Alfajores (testnet)   | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| KCC testnet                | `0x15D35b8985e350f783fe3d95401401E194ff1E6f` |
| Cronos testnet             | `0xBAEA4A1A2Eaa4E9bb78f2303C213Da152933170E` |
| Arbitrum Goerli (testnet)  | `0x939C0e902FF5B3F7BA666Cc8F6aC75EE76d3f900` |
| zkSync v2 Goerli (testnet) | `0xF532F2C1bB7b67E08f7D8B76f9fF804D0831725e` |
| Base Goerli (testnet)      | `0x5955C1478F0dAD753C7E2B4dD1b4bC530C64749f` |
| Shimmer testnet            | `0x354bF866A4B006C9AF9d9e06d9364217A8616E12` |
| Chiado (Gnosis testnet)    | `0xdDAf6D29b8bc81c1F0798a5e4c264ae89c16a72B` |
| EVMOS testnet              | `0x354bF866A4B006C9AF9d9e06d9364217A8616E12` |


## Price Feed IDs

The price feed IDs for EVM chains differs depending on whether they are a mainnet or testnet (see above):
* [List of mainnet ids](https://pyth.network/developers/price-feed-ids#pyth-evm-mainnet)
* [List of testnet ids](https://pyth.network/developers/price-feed-ids#pyth-evm-testnet)
