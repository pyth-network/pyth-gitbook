---
description: Consume Pyth Network prices in applications on Aptos
---

# Pyth on Aptos

## How Pyth on Aptos Works

Pyth prices are published on Pythnet and relayed to Aptos networks using the [Wormhole Network](https://wormholenetwork.com/) as a cross-chain message passing bridge. The Wormhole Network observes when Pyth prices on Pythnet have changed and publishes an off-chain signed message attesting to this fact. This process is explained in more detail [here](https://docs.wormholenetwork.com/wormhole/).

This signed price update message can then be submitted to the Pyth contract. The contract verifies the Wormhole message and updates the on-chain Pyth price to the new price.

Pyth does not automatically submit the prices to the Aptos networks; Protocols and users are responsible for updating the on-chain Pyth price before using it.

### On-demand Price Updates

When a consumer needs to use the value of a price, they should first submit the latest Wormhole update for that price to the Pyth contract on the Aptos network they are using. Updating prices on-demand will make the most recent price update available for contracts on that network.

This approach has many advantages for Pyth and its consuming protocols:

- Gas efficient: Prices will get updated only when they are needed. So no gas will be used to update a price that no one won't use.
- Access to low-latency prices: This approach allows protocols to use low-latency prices without sacrificing the gas. 
- More price feeds: By doing so, Pyth can publish thousands of price feeds without paying extra costs to submit them on-chain.

In this approach, protocols will update the prices in the same transaction that uses the prices. The calling contract method will:
  1. Receive the price update data as an argument.
  2. Update the on-chain Pyth prices.
  3. Query the on-chain Pyth prices for use on-chain.
 
The [pyth-aptos-js](https://github.com/pyth-network/pyth-js/tree/main/pyth-aptos-js) library makes it easy for users to craft the necessary price update transactions. The library documentation has a worked example showing how to write the on-chain program and the frontend code to use Pyth based on this model.

## Using Pyth On-Chain

Aptos contracts can update and fetch the Pyth prices using the Pyth Aptos Contract, which has been deployed on Testnet. The documented source code can be found [here](https://github.com/pyth-network/pyth-crosschain/blob/main/aptos/contracts/sources/pyth.move). A minimal example of how to update and use the Pyth on-chain prices can be found [here](https://github.com/pyth-network/pyth-crosschain/blob/main/aptos/example).

### Networks 

Pyth is currently deployed on Aptos Testnet, and will be available on Aptos Mainnet as soon as the chain is live.

### Addresses

When deploying contracts using Pyth, the [named addresses](https://diem.github.io/move/address.html#named-addresses) `pyth`, `wormhole` and `deployer` need to be defined at compile time.

| Network       | `pyth` Address                                                         |
| ------------- | -----------------------------------------------------------------------|
| Aptos Testnet | `0xaa706d631cde8c634fe1876b0c93e4dec69d0c6ccac30a734e9e257042e81541`   |

| Network       | `wormhole` Address                                                     |
| ------------- | -----------------------------------------------------------------------|
| Aptos Testnet | `0x1b1752e26b65fc24971ee5ec9718d2ccdd36bf20486a10b2973ea6dedc6cd197`   |

| Network       | `deployer` Address                                                     |
| ------------- | -----------------------------------------------------------------------|
| Aptos Testnet | `0xb138581594ebd7763cfa3c3e455050139b7304c6d41e7094a1c78da4e6761ed8`   |

`deployer` and `wormhole` are implementation details of the Pyth contract: you will not need to interact with these.

## Testnet Price Feed IDs

The full list of price feeds available on Aptos Testnet is available [here](https://pyth.network/developers/price-feed-ids/#pyth-cross-chain-testnet). As these are Testnet price feeds, their IDs will be different to the feeds available on Aptos Mainnet.
