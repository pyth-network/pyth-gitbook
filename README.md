# Introduction

Pyth Network is an oracle that publishes financial market data to multiple blockchains, where it can be used in on-chain applications.
Our market data is contributed by over 50 [first-party publishers](https://pyth.network/publishers/), including some of the biggest exchanges and market making firms in the world.
We offer price feeds for a number of different asset classes, including US equities, commodities, and cryptocurrencies.
You can find the full list of available price feeds [here](https://pyth.network/price-feeds/).
Our price feeds publish a [robust aggregate](how-pyth-works/price-aggregation.md) of publisher prices and update multiple times per second.

Our price feeds are available on multiple blockchains and can also be used in off-chain applications.
Price feeds are available in Solana mainnet and testnet for several EVM chains.
Prices will also be coming soon to Cosmos-based chains, and we are working to bring Pyth price feeds to many more chains in the near future.

## Get Started

We have several different guides to get started with Pyth, depending on your use case.
If you would like to consume Pyth data in on- or off-chain applications, please select the relevant guide below:

* [Solana](consumers/solana.md)
* [EVM](consumers/evm.md)
* [Off-chain applications](consumers/solana.md)

Publish first-party data to Pyth:
{% content-ref url="publishers/publish-data.md" %}
[publishers/publish-data.md](publishers/publish-data.md)
{% endcontent-ref %}

Dig in to the details of Pyth's architecture and design:
{% content-ref url="how-pyth-works/how-pyth-works.md" %}
[how-pyth-works/how-pyth-works.md](how-pyth-works/how-pyth-works.md)
{% endcontent-ref %}
