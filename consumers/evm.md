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
| Goerli (Ethereum testnet) | |
| Ropsten (Ethereum testnet) | |
| Fuji (Avalanche testnet) | |
| Fantom testnet | |
| Mumbai (Polygon testnet) | |
| BNB testnet | |
| -- | -- |

## Price Feed IDs

All EVM chains share the same price feed IDs, which are listed [here](https://pyth.network/developers/price-feed-ids/#binance-smart-chain-testnet)
