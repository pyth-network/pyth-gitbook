# Price Service

The [price service][price-service-repo] is a webservice that listens to the Wormhole Network for Pyth price updates and serves them via a convenient web API.
The service allows users to easily query for recent price updates via a REST API, or subscribe to a websocket for streaming updates.
The Pyth Network Javascript SDKs connect to an instance of the price service in order to fetch on-demand price updates.

## Public Endpoints

The Pyth Data Association operates two public endpoints for the price service, for mainnet and testnet respectively.
These endpoints can be used to test integrations with Pyth Network:

| network | url                             |
| ------- | ------------------------------- |
| mainnet | https://xc-mainnet.pyth.network |
| testnet | https://xc-testnet.pyth.network |

For production deployments, developers integrating with Pyth Network are **strongly encouraged** to host their own instance of the price service for maximum resilience and decentralization.
By running an independent instance of this service, developers tap directly into Wormhole's peer-to-peer network to stream Pyth price updates.
This peer-to-peer network has built-in redundancy and is therefore inherently more reliable than a centralized service operated by the PDA.
Please find more information about building and running the price service from [here][price-service-repo].

[price-service-repo]: https://github.com/pyth-network/pyth-crosschain/tree/main/price-service
