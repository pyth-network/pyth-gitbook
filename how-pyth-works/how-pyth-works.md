# How Pyth Works

The Pyth network is a next-generation oracle that aims to bring accurate, high-frequency financial market data to blockchain applications.
The network does so by incentivizing market participants — trading firms, market makers, and exchanges — to share directly on-chain the price data collected as part of their existing operations.
Pyth's data providers include some of the largest **traders**, **exchanges**, and **financial services** players who create unique high quality market data.
This includes real world market data in **equities**, **fx, crypto, and metals with ambitions to scale across asset classes**.
Data providers include Jump Trading Group, [GTS](https://pythnetwork.medium.com/new-pyth-data-provider-gts-555c4d0e362b), Alameda, Jane Street, Hudson River Trading, [LMAX](https://pythnetwork.medium.com/new-pyth-data-provider-lmax-dd05264d1a16), [Virtu](https://pythnetwork.medium.com/new-pyth-data-provider-virtu-financial-ed09143f44d5), [BSX](https://pythnetwork.medium.com/new-pyth-data-provider-the-bermuda-stock-exchange-ccf3c04bd430), [Genesis Global Trading](https://pythnetwork.medium.com/new-pyth-data-provider-genesis-global-trading-dcd8ec97bffd), [FTX](https://pythnetwork.medium.com/new-pyth-data-provider-ftx-6a2cfdeffd02), [CTC](https://pythnetwork.medium.com/new-pyth-data-provider-chicago-trading-company-64a457340443), and [many more](https://pyth.network/publishers/).

The protocol is an interaction between three parties:

1. _Publishers_ submit pricing information to Pyth's on-chain program. Pyth has multiple data publishers for every product to improve the accuracy and robustness of the system.&#x20;
2. Pyth's _on-chain program_ combines publishers' data to produce a single aggregate price and confidence interval.
3. _Consumers_ read the price information produced by the on-chain program.

The Pyth program maintains a number of different [Solana accounts](account-structure.md) that list the products on Pyth and their current price data. Publishers publish their price and confidence by interacting with the on-chain program on every slot. The program stores this information in its accounts. The first price update in a slot additionally triggers [price aggregation](price-aggregation.md), which combines the price data from the previous slot into a single aggregate price and confidence interval. This aggregate price is written to the Solana account where it is readable by other on- and off-chain programs (see [Client Libraries](../consumers/client-libraries.md) for how to use this data).&#x20;