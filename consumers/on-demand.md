# On-Demand Price Updates

Pyth Network uses an on-demand price update model that is slightly different from other oracles you may be more familiar with.
Most oracles today use a push model, where the oracle runs an off-chain process that continuously sends transactions to update an on-chain price.
In contrast, Pyth Network does not operate an off-chain process that pushes prices on-chain.
Instead, it delegates this work to Pyth Network users.
Pyth price updates are streamed off-chain via the Wormhole Network, a cross-chain messaging protocol.
These updates are signed such that the Pyth on-chain program can verify their authenticity.
Updating the on-chain price is a *permissionless* operation: anyone can submit a valid Wormhole message to the Pyth contract to update the price.
Typically, users of Pyth Network prices will submit a single transaction that simultaneously updates the price and uses it in a downstream application.

## Advantages

The on-demand model has several benefits over the push model:

- **Gas efficiency** -- On-chain prices are only updated when they are needed.
  In the push model, the oracle can waste gas by submitting price updates that no one will use.
  Furthermore, the cost of updating the oracle is distributed amongst its users instead of borne entirely by Pyth Network.
  The cost of maintaining the on-chain prices can be substantial for a single entity, but is minimal when spread across all users.
  Many of the subsequent advantages follow from the fact that Pyth Network does not have to pay gas fees for every single update.
- **High update frequency** -- Pyth Network price feeds update once per second, which is faster than the blocktime of most blockchains.
  Such frequent updates would not be possible if every price had to be pushed on-chain.
  However, push oracles typically update even less frequently than the blocktime, because it is simply too expensive to update feeds more frequently.
- **Low latency** -- Every transaction can use a recent off-chain price, instead of relying on the last on-chain update pushed by the oracle itself.
- **More price feeds** -- Pyth Network can scale to thousands of price feeds due to its gas efficiency.
  The oracle incurs no added costs for each additional feed, and users pay gas costs for new feeds only when those feeds are used on-chain.
- **Common infrastructure** -- Every component of Pyth Network is *shared across blockchains* except for the contract deployed on the destination chain.
  These shared components can therefore be built with high reliability and accuracy targets, benefitting every chain the oracle is deployed on.
  This approach also allows Pyth Network to rapidly launch on new blockchains and ecosystems with all of the existing price feeds.
- **Sustainable** -- The Pyth Network protocol has been designed to allow for the optional enablement of data fees to update the state of an on-chain price feed.
  These fees will compensate data providers for their effort and motivates them to contribute additional data.
  Oracles without such a mechanism are inherently unsustainable and likely to fail if the operating organization runs out of money.

## Integration

Developers integrating with Pyth Network should build their application to submit the necessary price updates on their users' behalf.
For example, if you need the BTC/USD price on-chain, then your frontend should submit the BTC/USD Pyth price update in every transaction that needs it.
The [Pyth Network SDKs](consume-data.md) cover both parts of this integration -- frontend and contract -- and are designed to simplify this process.

## Fees

The Pyth Network protocol has been designed to allow for the optional enablement of data fees in order to update the state of an on-chain price feeds.
The ongoing existence of and size of the fee will be determined by governance on a per-blockchain basis; until governance is live, the fee will be 1 of the smallest denomination of the blockchain's native token (e.g., 1 wei on Ethereum).
The fees collected by the protocol will go toward compensating data providers and possibly other uses as determined by governance.

Note that protocols integrating with Pyth Network can pass these fees along to their users.
Whenever a user submits a transaction that requires a price update, that transaction can also include payment of the necessary fee.
This approach charges end users in proportion to their usage of Pyth Network data.
The Pyth Network SDKs use this approach by default and include all of the necessary logic for computing and sending the fee along with every transaction.

In addition to update fees, end users ultimately bear the gas cost of updating the Pyth Network price feeds, which means that their transactions cost a little more than they would in the push model.
However, the cost of a single price update is minimal, so the combined gas and update fee should only be a small portion of the overall transaction cost for the end user.

## Adversarial selection

On-demand price updates gives users of Pyth Network some ability to select which price to use in a transaction.
This ability is highly circumscribed by various constraints: on-chain prices must move forward in time, and cannot be from too far in the past.
However, users can still chose any price update that satisfies these constraints.
This ability is functionally equivalent to latency: it allows users to see the price in the future before using a price from the past. 

The simplest way to guard against this attack vector is to incorporate a staleness check to ensure that the price used in a transaction is sufficiently recent.
The Pyth Network SDKs include this check by default, where queries for the price will fail if the on-chain time differs from the price's timestamp by more than a threshold amount.
Highly latency-sensitive protocols may wish to tune this threshold to suit their needs.
Protocols may take additional measures to ensure that they are not using stale prices.
