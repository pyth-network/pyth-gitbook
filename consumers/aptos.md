---
description: Consume Pyth Network prices in applications on Aptos
---

# Pyth on Aptos

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
