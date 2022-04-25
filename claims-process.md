---
description: >-
  For more information, visit the Pyth whitepaper
  https://pyth.network/whitepaper
---

# Claims Process

One should expect there to be times where the Pyth network must verify and resolve apparent conflicts between an on-chain aggregated market price that may be deemed erroneous when compared to real-world reference prices.

A seemingly obvious yet subtle point: when a set of publishers quotes potential outlier prices which then generates an aggregate price that consumers deem to be wrong, the network must determine whether those who paid data fees must receive a payout. If the aggregated price is ratified as wrong, the specific at-fault publishers are identified, and their stakes are slashed and paid out to the end-users.

Overall, the claims process will determine whether a payout occurs. The purpose of this process is to verify that the aggregate price and confidence interval for a product were incorrect in comparison to some ground-truth off-chain data. The process will use [HUMAN protocol](https://medium.com/human-protocol/introduction-to-the-human-protocol-304b1448d772) — an open-source software package provided by Pyth — to collect the necessary off-chain information from impartial judges and then feed that information into a predetermined algorithm that determines the outcome of the claim. Finally, PYTH token-holders will vote to ratify the output of the algorithm.

Anyone will be able to file a claim against the protocol to (possibly) trigger a payout by bonding PYTH tokens. The latter is returned if the claim is ratified by governance; this requirement prevents spam.

![](<.gitbook/assets/Screenshot 2022-03-03 125900.jpg>)
