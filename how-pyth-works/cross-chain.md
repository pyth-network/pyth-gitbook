# Cross-chain

Pyth needs a cross-chain component to ferry prices on [Pythnet](pythnet.md) to target chains. The diagram below shows how prices are delivered from Pythnet to target chains.

![](<../.gitbook/assets/pythnet_schema.png>)

Pyth Network uses a “pull” update model for target chain prices: instead of continually pushing updates to each target chain, users pull the prices on-chain when they are needed. This pull model is highly scalable and allows Pyth Network to deliver high-frequency price updates for a large number of products without overwhelming the transaction capacity of target chains (or incurring excessive gas fees).

The pull model updates target chain prices using the following process. The price service continually listens to Wormhole for Pyth price update messages. It stores the latest update message in memory and exposes HTTP and websocket APIs for retrieving the latest update. (Anyone can run an instance of this webservice, but the Pyth Data Association runs a public instance for convenience.) When a user wants to use a Pyth price in a transaction, they retrieve the latest update message from the price service and submit it in their transaction. The target chain Pyth contract will verify the validity of the price update message and, if it is valid, store the new price in its on-chain storage.   

Finally, on-chain protocols integrate with the Pyth contract via a simple API that retrieves the current Pyth price from its on-chain storage. This API will return the current price as long as it has been updated sufficiently recently; this approach works because users will have updated the Pyth price earlier in the same transaction. Protocols can configure the recency threshold to suit their needs — e.g., latency sensitive applications can set a lower threshold than the default.





