---
description: How Pyth Network provides crosschain prices
---

# Pyth Crosschain

Pyth prices are published on Pythnet and relayed to Aptos networks using the [Wormhole Network](https://wormholenetwork.com/) as a cross-chain message passing bridge. The Wormhole Network observes when Pyth prices on Pythnet have changed and publishes an off-chain signed message attesting to this fact. This process is explained in more detail [here](https://docs.wormholenetwork.com/wormhole/).

This signed price update message can then be submitted to the Pyth contract. The contract verifies the Wormhole message and updates the on-chain Pyth price to the new price.

Pyth does not automatically submit the prices to the Aptos networks; Protocols and users are responsible for updating the on-chain Pyth price before using it.

### On-demand Price Updates

When a consumer needs to use the value of a price, they should first submit the latest Wormhole update for that price to the Pyth contract on the Aptos network they are using. Updating prices on-demand will make the most recent price update available for contracts on that network.

This approach has many advantages for Pyth and its consuming protocols:

- Gas efficient: Prices will get updated only when they are needed. So no gas will be used to update a price that no one will use.
- Access to low-latency prices: This approach allows protocols to use low-latency prices without sacrificing the gas. 
- More price feeds: By doing so, Pyth can publish thousands of price feeds without paying extra costs to submit them on-chain.

In this approach, protocols will update the prices in the same transaction that uses the prices. The calling contract method will:
  1. Receive the price update data as an argument.
  2. Update the on-chain Pyth prices.
  3. Query the on-chain Pyth prices for use on-chain.
 
The [pyth-aptos-js](https://github.com/pyth-network/pyth-js/tree/main/pyth-aptos-js) library makes it easy for users to craft the necessary price update transactions. The library documentation has a worked example showing how to write the on-chain program and the frontend code to use Pyth based on this model.

