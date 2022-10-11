# On-Demand Price Updates

Pyth Network's on-demand price update model contrasts with other oracles that use a push model.
In the push model, the oracle runs an off-chain process that continuously sends transactions to update an on-chain price.
Updating the on-chain price is a permissioned operation that can only be performed by the oracle itself.
In contrast, Pyth Network does not operate such a process and instead delegates this work to Pyth Network users.
Pyth price updates are streamed off-chain via the Wormhole Network, a cross-chain messaging protocol.
These updates are signed in such a way that the Pyth on-chain program can verify their authenticity.
Typically, users of Pyth Network prices will submit a single transaction that simultaneously updates the price and uses it.


## Advantages

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

Developers need to build their application to submit price updates on behalf of their users, which typically requires integrating with both the frontend and contract.
The [Pyth Network SDKs](consume-data.md) cover both parts of this integration and are designed to simplify this process.

## Fees

The Pyth Network protocol has been designed to allow for the optional enablement of data fees in order to update the state of an on-chain price feeds.
The ongoing existence of and size of the fee will be determined by governance on a per-blockchain basis; until governance is live, the fee will be 1 of the smallest denomination of the blockchain's native token (e.g., 1 wei on Ethereum).
The fees collected by the protocol will go toward compensating data providers and possibly other uses as determined by governance.

Note that protocols integrating with Pyth Network can pass these fees along to their users.
Whenever a user submits a transaction that requires a price update, that transaction can also include payment of the necessary fee.
This approach charges end users in proportion to their usage of Pyth Network data.
The Pyth Network SDKs use this approach by default and include all of the necessary logic for computing and sending the fee along with every transaction.

In addition to update fees, end users ultimately bear the gas cost of updating the Pyth Network price feeds, which means that their transactions cost a little more than they would in the push model.
However, the cost of a single price update is minimal; it is only expensive when added up across time and feeds.
The gas and update fee should be only a small portion of the overall transaction cost for the end user.

## Adversarial selection** -- Users of Pyth Network have some ability to select which price to use in a transaction.
  This ability is highly circumscribed by various constraints: prices must move forward in time, and cannot be from too far in the past.
  However, users can still chose any price update that satisfies these constraints.
  This ability is functionally equivalent to additional latency on the oracle price; highly latency-sensitive protocols should take additional measures to ensure that they are not using stale prices.
  One possible measure is to operate an off-chain service that pushes price updates when the price moves substantially.
- **End user transaction cost** -- 
  

