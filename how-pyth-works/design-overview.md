# Design Overview

Pyth is a protocol that allows market participants to publish pricing information on-chain for others to use. The protocol is an interaction between three parties:

1. _Publishers_ submit pricing information to Pyth's on-chain program. Pyth has multiple data publishers for every product to improve the accuracy and robustness of the system.&#x20;
2. Pyth's _on-chain program_ combines publishers' data to produce a single aggregate price and confidence interval.
3. _Consumers_ read the price information produced by the on-chain program.

Pyth's on-chain program runs simultaneously on both Solana mainnet and [Pythnet](pythnet.md).
Pythnet is an appchain used to aggregate the prices delivered to all other blockchains.
In both cases, the Pyth program maintains a number of different [Solana accounts](account-structure.md) that list the products on Pyth and their current price data.
Publishers publish their price and confidence by interacting with the on-chain program on every slot. The program stores this information in its accounts.
The first price update in a slot additionally triggers [price aggregation](price-aggregation.md), which combines the price data from the previous slot into a single aggregate price and confidence interval.
This aggregate price is written to the Solana account where it is readable by other on- and off-chain programs (see [Client Libraries](../consumers/client-libraries.md) for how to use this data).&#x20;
