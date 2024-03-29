---
description: >-
  For more information, visit the Pyth whitepaper
  https://pyth.network/whitepaper
---

# Network Interactions

The Pyth protocol consists of 4 on-chain core mechanisms:

* **Price aggregation** combines the reported prices and confidence intervals of individual publishers into a single price feed and confidence interval feed for a specific product (e.g. BTC/USD feed). This mechanism is designed to produce robust price feeds — feeds whose prices cannot be significantly influenced by small groups of publishers.
* **Data staking** allows delegators to stake tokens to earn data fees. The delegators in aggregate also determine the level of influence (stake-weight) that each publisher has on the aggregate price. In addition, this mechanism determines whether delegators’ stakes are slashed. Finally, the mechanism collects data fees from consumers and distributes a share to delegators (initially set at 80%). The remainder (20%) goes into a reward pool that is distributed among publishers.
* **Reward distribution** determines the share of the reward pool earned by each publisher. Each product has a reward pool that delegators can stake into. The reward distribution mechanism preferentially rewards publishers with higher quality price feeds and reduces the likelihood that uninformed publishers will earn rewards.
* **Governance** will be using a coin-voting system that will help determine the high-level parameters of the three mechanisms above. Parameters include what types of tokens may be used for data fees; which products are listed on Pyth; the share of data fees allocated to publishers, delegators, and other uses; the number of PYTH tokens that publishers must stake or enable claims to be filed against a product, and more.

![](<.gitbook/assets/Screenshot 2022-03-03 125644.jpg>)
