# Consume Price Feeds

Pyth Network uses an on-demand pricing model where users are responsible for posting price updates on-chain when needed.
In this model, Pyth Network does not continuously update the price feeds on most chains.
Instead, Pyth prices are streamed off-chain via the Wormhole cross-chain messaging protocol.
Each supported blockchain hosts a Pyth program that supports a permissionless price update operation; this operation accepts a Wormhole message, verifies its content, and updates an on-chain price stored in the program.
Users of Pyth are responsible for invoking this permissionless update when they wish to use Pyth price.
For a discussion of the costs and benefits of this model, see [_Why on-demand updates_](why-on-demand.md).

In the on-demand model, developers should integrate Pyth into both their on-chain and off-chain code:
1. On-chain programs should read prices from the Pyth program deployed on the same chain
2. Off-chain frontends and jobs should include Pyth price updates alongside (or within) their application-specific transactions.

Pyth provides ecosystem-specific SDKs to assist with both the on- and off-chain pieces of the integration.
The easiest way to use Pyth price feeds is to integrate the appropriate SDKs into your application.
Before getting started with an SDK, please read [_Introduction to Price Feeds_](best-practices.md) to understand how Pyth price feeds are represented, and to learn best practices to use Pyth prices safely and correctly.
Then, follow the links below to find the right SDK for your ecosystem:

{% content-ref url="solana.md" %}
[solana.md](solana.md)
{% endcontent-ref %}

{% content-ref url="evm.md" %}
[evm.md](evm.md)
{% endcontent-ref %}

{% content-ref url="aptos.md" %}
[aptos.md](aptos.md)
{% endcontent-ref %}

{% content-ref url="bas.md" %}
[bas.md](bas.md)
{% endcontent-ref %}

{% content-ref url="off-chain.md" %}
[off-chain.md](off-chain.md)
{% endcontent-ref %}
