---
description: Consume Pyth Network prices in applications on EVM-based chains
---

# Pyth on EVM

## How Pyth Works on EVM Chains

Pyth prices are published on Solana and relayed to EVM chains using the [Wormhole Network](https://wormholenetwork.com/) as a cross-chain message passing bridge. The Wormhole Network observes when Pyth prices on Solana have changed and publishes an off-chain signed message attesting to this fact. This process is explained in more detail [here](https://docs.wormholenetwork.com/wormhole/).

This signed price update message can then be submitted to the Pyth contract. The contract verifies the Wormhole message and updates the on-chain Pyth price to the new price.

Pyth does not automatically submit the prices to the EVM networks; Protocols and users are responsible for updating the on-chain Pyth price before using it.

There are two different ways for protocols to perform these updates:

### On-demand price updates

When a consumer needs to use the value of a price, they should first submit the latest Wormhole update for that price to the Pyth contract on their target EVM network. Updating prices on-demand will make the most recent price update available for EVM contracts to use.

This approach has many advantages for Pyth and its consuming protocols:

- Gas efficient: Prices will get updated only when they are needed. So no gas will be used to update a price that no one won't use.
- Access to low-latency prices: This approach allows protocols to use low-latency prices without sacrificing the gas. 
- More price feeds: By doing so, Pyth can publish thousands of price feeds without paying extra costs to submit them on-chain.

In this approach, protocols will update the prices in the same transaction that uses the prices. The calling contract method will get the prices update data as an argument, (1) update the on-chain Pyth prices, and (2) use the prices in the contract. The [pyth-evm-js](https://github.com/pyth-network/pyth-js/tree/main/pyth-evm-js) library makes it easy for users to craft the necessary price update transactions. The library documentation has a worked example showing how to write the on-chain program and the frontend code to use Pyth based on this model.

### EVM price pusher

[Pyth EVM price pusher](https://github.com/pyth-network/pyth-js/tree/main/pyth-evm-price-pusher)
is a service that regularly pushes price updates to the on-chain Pyth contract. Protocols can run this service to push regular updates to the on-chain
Pyth price based on their desired time. Protocols can configure the frequency and conditions of pushing price updates to the EVM network as desired. This service is useful for protocols that already depend on regular push updates and want to facilitate their migration to Pyth. Please see the price pusher documentation for more information on its usage.

## How to use Pyth on-chain

On-chain programs can use our [Solidity SDK](https://github.com/pyth-network/pyth-sdk-solidity) to read Pyth prices.
Please see the SDK documentation for more information on expected usage and example code.

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

All EVM chains share the same price feed IDs, which are listed [here](https://pyth.network/developers/price-feed-ids/#pyth-cross-chain-testnet)
