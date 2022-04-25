# Price Aggregation

As background, Pyth is an oracle that publishes an aggregate price and confidence interval for each product on every Solana slot. The Pyth program computes this price on-chain by aggregating the prices and confidence intervals submitted by individual publishers.

**We want Pyth’s aggregation algorithm to have 3 properties:**

**#1 Robust to manipulation**

_If most publishers are submitting a price of $100 and one publisher submits a price of $80, the aggregate price should remain near $100 and not be overly influenced by the single outlying price._

![](<../.gitbook/assets/https\_\_\_bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com\_public\_images\_8c7da880-4157-4543-a293-37b5f5bfdac1\_291x172 (1).jpeg>)

**#2 Aggregate price should appropriately weight data sources with different levels of accuracy**

_Pyth allows publishers to submit a confidence interval because they have varying levels of accuracy in observing the price of a product. This property can result in situations where one publisher reports a price of $101 +/- 1, and another reports $110 +/- 10. In these cases, we would like the aggregate price to be closer to $101 than $110._

![](<../.gitbook/assets/https\_\_\_bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com\_public\_images\_c0ab7e74-adb8-4324-9ef1-607c41bde1d4\_292x171 (1).jpeg>)

**#3 Aggregate confidence interval should reflect the variation between publishers’ prices**

_In reality, there is no single price for any given product. Every product trades at a slightly different price around the world and so we must be able to reflect these variations._

![](<../.gitbook/assets/https\_\_\_bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com\_public\_images\_0b4c8b1e-26bb-4131-8e2b-f725839d1bad\_577x181 (1).jpeg>)

**How does the aggregation algorithm achieve the 3 above properties?**

The first step of the algorithm computes the aggregate price by giving each publisher three votes — one vote at their price and one vote at each of their price +/- their confidence interval — then taking the median of all the votes.&#x20;

The second step computes the distance from the aggregate price to the 25th and 75th percentiles of the votes, then selects the larger of the two as the aggregate confidence interval. Now, let’s put everything together and visualize it with 4 scenarios.

_In the following graphs, the red star depicts the aggregate price and the bold red line depicts the aggregate confidence interval. The grey circles represent the 25th and 75th percentiles of the votes — the further one of these from the aggregate price determines the confidence interval’s width._

* Scenario 1

One “confident” publisher (tight confidence interval) is an outlier to the cohort but does not impact the final aggregated price. Its only impact will be a greater aggregated confidence interval that could highlight a price dislocation of the asset on different venues.

![](<../.gitbook/assets/https\_\_\_bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com\_public\_images\_a48fd6dc-356f-49fc-975a-290042f368e6\_252x292 (1).jpeg>)

* Scenario 2

It demonstrates how publishers with tighter confidence intervals (while having overlapping quotes with the rest of the cohort) can exert greater influence over the location of the aggregate price.

![](<../.gitbook/assets/https\_\_\_bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com\_public\_images\_26665263-76ef-43e7-ad50-37b7b3f2775a\_250x295 (1).jpeg>)

* Scenario 3

It features publishers in overall “agreement” regarding the price and their relative uncertainty towards it. The final result shows that the aggregate confidence interval accounts for each publishers’ CI and gives identical results to the ordinary median.

![](<../.gitbook/assets/https\_\_\_bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com\_public\_images\_8a2812c7-73d9-4d3f-8058-d5489ec3407b\_230x290 (1) (1).jpeg>)

* Scenario 4

Publishers publish distinct prices with non-overlapping confidence intervals. In this case, all votes of a single publisher will be adjacent in the sorted list and will be treated as a single vote.

![](<../.gitbook/assets/https\_\_\_bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com\_public\_images\_812a2656-0c46-4b64-9538-fccb364cb343\_260x283 (1).jpeg>)

**Even if we would not be in any of the above scenarios mentioned, the aggregate price will always lie within the 25th-75th percentile of the publisher’s prices.**

In addition, we’re working on a staking system for publishers that incentivizes them to provide accurate data, and in that system, each publisher will have a varying amount of stake. All of the results also hold for stake weights if we simply replace the % of publishers with the % of stake controlled.

Note that in the future the weight calculation can be extended to include other non-price factors such as quoter stake (mentioned above), historical quoter performance, and many other relevant metrics.
