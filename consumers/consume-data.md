# Consume Price Feeds

We provide a variety of SDKs for consuming Pyth price feeds in both on- and off-chain applications.
For on-chain programs, there is a Pyth program deployed on each chain that stores all of our price data.
Our SDKs allow on-chain programs to access this information in a simple way.
The SDKs also implement some best practices to protect users from accidentially reading stale prices and other common programming errors.

In order to save gas and reduce chain congestion, Pyth Network does not continuously update the price feeds on most chains.
Instead, Pyth prices are streamed via the Wormhole cross-chain messaging protocol.
Users of Pyth are responsible for submitting the relevant Wormhole message to the on-chain Pyth program to update its price.
We recommend that users incorporate this price update operation into the same transaction as the one consuming the price.
Frontend applications can use the [pyth-js](https://github.com/pyth-network/pyth-js) library to construct and submit these messages on behalf of their users.

The full list of Pyth Network price feeds is listed on the [pyth.network website](https://pyth.network/price-feeds/).
To consume a particular price feed on-chain, you will need to look up its price feed ID.
This ID uniquely identifies this particular price feed and is required to query the Pyth on-chain program to obtain the current price.
However, the ID may be stored in different formats depending on the target chain.
The [price feed IDs page](https://pyth.network/developers/price-feed-ids) lists the ID of each available price feed on every chain where they are available.

{% hint style="info" %}
We recommend reading the [_Using Price Feeds_](best-practices.md) guide to ensure you are using price feeds safely and correctly.
{% endhint %}

{% content-ref url="solana.md" %}
[solana.md](solana.md)
{% endcontent-ref %}

{% content-ref url="evm.md" %}
[evm.md](evm.md)
{% endcontent-ref %}

{% content-ref url="bas.md" %}
[bas.md](bas.md)
{% endcontent-ref %}

{% content-ref url="off-chain.md" %}
[off-chain.md](off-chain.md)
{% endcontent-ref %}
