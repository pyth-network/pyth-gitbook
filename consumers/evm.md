---
description: Consume Pyth Network prices in applications on EVM-based chains
---

# Pyth on EVM

On-chain programs can use our [Solidity SDK](https://github.com/pyth-network/pyth-sdk-solidity) to read Pyth prices.
Please see the SDK documentation for more information on expected usage and example code.

On EVM-based chains, Pyth users are responsible for updating Pyth prices as needed.
The [pyth-evm-js](https://github.com/pyth-network/pyth-js/tree/main/pyth-evm-js) library makes it easy for users to craft the necessary price update transactions.
The library documentation has a worked example showing how to write both the on-chain program and frontend code to use Pyth.

## Networks

Pyth is currently available on the following EVM-based chains:

| Network | Contract address |
| -- | -- |
| Goerli (Ethereum testnet) | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Ropsten (Ethereum testnet) | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Fuji (Avalanche testnet) | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Fantom testnet | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| Mumbai (Polygon testnet) | `0xff1a0f4744e8582DF1aE09D5611b887B6a12925C` |
| BNB testnet | `0xd7308b14BF4008e7C7196eC35610B1427C5702EA` |
| Aurora testnet | `0x4305FB66699C3B2702D4d05CF36551390A4c69C6` |

## Price Feed IDs

All EVM chains share the same price feed IDs, which are listed [here](https://pyth.network/developers/price-feed-ids/#binance-smart-chain-testnet)

