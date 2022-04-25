---
description: Best practices for consuming Pyth data
---

# Best Practices

This page explains best practices for designing protocols that consume Pyth's price and confidence interval. Our suggestions are as follows:

1. Use products with at least 3 active publishers.
2. Check the status of the product
3. Use the confidence interval to protect your users from price uncertainty

**Active Publishers**

Pyth produces its price by aggregating price information from several different publishers. Each product in Pyth has a different number of publishers who are currently submitting prices. If a product has more publishers, each publisher has less influence on the overall price, which results in a more reliable aggregate price. If there are fewer than three publishers, then those publishers exert a substantial influence on the aggregate price.

Before consuming a price feed, we suggest consulting the page for that product and determining how many publishers are actively submitting prices. For example, the BTC/USD product page is here: [https://pyth.network/markets/#BTC/USD](https://pyth.network/markets/#BTC/USD). If there are fewer than three publishers, we do not suggest using that price feed for high-value applications at the moment. We are working on adding more publishers to these products, and these feeds will become more robust over time.

**Check Product Status**

Sometimes, Pyth will not have a valid price for a product. This situation can happen for various reasons. For example, US equity markets only trade during certain hours, and outside those hours, it's not clear what an equity's price is. Alternatively, Solana congestion may prevent data publishers from being able to submit their prices. During these periods, Pyth will not have a valid price for a product.

Pyth's price accounts have a `status` field that indicates whether or not the price is valid. A status of `trading` indicates a valid price that is permissible to use in downstream applications. If the status is not `trading`, the Pyth price can be **an arbitrary value**. Protocols should check the status field before consuming the price -- or use a client library that does this automatically -- and gracefully handle the case when pricing is currently unavailable.&#x20;

**Confidence Intervals**

At every point in time, Pyth publishes both a price and a confidence interval for each product. For example, Pyth may publish the current price of bitcoin as $50000 ± $10. Pyth publishes a confidence interval because, in real markets, there is _no one single price for a product_. For example, at any given time, bitcoin trades at different prices at different venues around the world. While these prices are typically similar, they can diverge for a number of reasons, such as when a cryptocurrency exchange block withdrawals on an asset. If this happens, prices diverge because arbitrageurs can no longer bring prices across exchanges into line. Alternatively, prices on different venues can differ simply because an asset is highly volatile at a particular point in time. At such times, bid/ask spreads tend to be wider, and trades on different markets at around the same time tend to occur at a wider range of prices.

Pyth represents these possibly-different prices by giving its users a _probability distribution over price_ instead of just a single price. The price of the product is drawn from a normal distribution centered on the Pyth price with a standard deviation equal to the confidence interval. If markets are behaving normally, then the confidence interval will be tight -- typically much less than 1% of the price -- and the normal distribution will be highly peaked. However, at unusual times, the confidence interval can widen out dramatically.

When consuming Pyth prices, we recommend using the confidence interval to protect your users from these unusual market conditions. The simplest way to do so is to use Pyth's confidence interval to compute a _range_ in which the true price (probably) lies. You obtain this range by adding and subtracting a multiple of the confidence interval to the Pyth price; the bigger the multiple, the more likely the price lies within that range. We recommend considering a multiple of 3, which gives you a 99.7% probability that the true price is within the range (assuming normal distribution estimates are correct). Then, _select the most conservative price within that range for every action._ In other words, your protocol should minimize state changes during times of large price uncertainty.

This principle is common sense. Imagine that you are lending money to a friend, and your friend pledges a bitcoin as collateral. Also imagine that Pyth says the bitcoin price is $50000 +- $1000. (Note that $1000 is an unusually large confidence interval for bitcoin; the confidence interval is typically \~$50 dollars). You therefore calculate that the true price is between $47000 and $53000 using the multiply by 3 rule from above. When originating the loan, you would value the bitcoin at $47000. The lower price is conservative in this instance because it limits the amount of borrowing that is possible while the price is uncertain. On the other hand, once the loan has been issued, you would value the bitcoin at $53000. The higher price is conservative, as it prevents you from liquidating your friend purely due to increased price uncertainty.

The same principle would apply if you wrote a derivative contract. If someone wants to open a derivative contract with you, you would value their collateral at the lower price. However, if you were deciding whether someone's margin limits were violated, you would value their collateral at the higher price. If a contract needs to be settled at a price, you could take approaches such as the following:

1. Using Pyth's exponential moving average price, which represents estimates of the average price of the asset over a specified time period (e.g., over the past 1 hour). The exponential moving average price is computed such that it lessens the influence of prices with wide confidence intervals. You may find more details in [ema-price-aggregation.md](../how-pyth-works/ema-price-aggregation.md "mention").
2. Using the aggregate price, which is Pyth's best estimate of the price at a single point in time. The quality of this estimate depends on the width of the confidence interval at settlement time and on occasion, it may be imprecise. However, it is the best you can do with Pyth data if you need a single price at that exact point in time.
3. Defining the contract to depend on confidence. For example, you could create an option that refunds the option premium to the buyer (so both sides of the transaction are even) if the strike price is within the confidence interval at settlement time. You could also create a contract that delayed settlement until the confidence interval was sufficiently small. If you choose this second option, you should ensure that your contract is guaranteed to eventually settle even if the confidence interval never narrows.
