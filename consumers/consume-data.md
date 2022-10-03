# Consume Price Feeds

The easiest way to use Pyth price feeds is to integrate the appropriate SDK into your application.
There are separate SDKs for each blockchain ecosystem and for off-chain use.
The links at the bottom of the page will point you to the right SDK for your use case.
The SDKs also implement best practices to protect users from accidentially reading stale prices and other common programming errors.

In order to save gas and reduce chain congestion, Pyth Network does not continuously update the price feeds on most chains.
Instead, Pyth prices are streamed off-chain via the Wormhole cross-chain messaging protocol.
Each supported blockchain hosts a Pyth program that supports a permissionless price update operation; this operation accepts a Wormhole message, verifies its content, and updates an on-chain price stored in the program.
Users of Pyth are responsible for invoking this permissionless update when they wish to use Pyth price.
Most integrators should combine the price update into the same transaction that uses the price.
The SDKs linked below help integrators craft the necessary transactions.

Each Pyth Network price feed has a unique id that applications use to look up the current price.
However, the ids can be represented in different formats (e.g., hex or base58) depending on the blockchain.
The full list of price feeds is listed on the [pyth.network website](https://pyth.network/price-feeds/).
The [price feed ids page](https://pyth.network/developers/price-feed-ids) lists the id of each available price feed on every chain where they are available.
To consume a particular price feed on-chain, look up its id using these pages, then store the id in your program to use for price feed queries.

{% hint style="info" %}
Please see the [_Using Price Feeds_](best-practices.md) guide to ensure you are using price feeds safely and correctly.
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
