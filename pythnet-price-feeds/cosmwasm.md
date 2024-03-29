---
description: Consume Pyth Network prices in applications on Cosmwasm
---

# Pyth on Cosmwasm

Cosmwasm contracts can update and fetch the Pyth prices using the Pyth Cosmwasm Contract, deployed on their network. The documented source code can be found [here](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/cosmwasm/contracts/pyth).

## Update Price Feeds
The mechanism by which price feeds are updated on Cosmwasm is explained [here](./pythnet-price-feeds.md). The [pyth-common-js](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/cosmwasm/sdk/js) can be used to fetch the latest price feed data which then can be passed to the `ExecuteMsg` on-chain function.

Pyth publishes prices for two kinds of feeds: 
1. Stable price feeds consist of prices generated on the pythnet blockchain. These feeds are available on both mainnet and testnet blockchains. Use stable feeds if you would like your test environment to be identical to your production environment.
2. Edge price feeds consist of prices generated on the pythtest blockchain, which is Pyth's test environment for new features. Consequently, these feeds are not as reliable as the stable feeds, and there are other differences as well (e.g., different price feed ids). These feeds are only available on testnets.

## Examples

- [Minimal on-chain contract](https://github.com/pyth-network/pyth-crosschain/blob/main/target_chains/cosmwasm/examples/cw-contract) which queries the Pyth contract.

## Networks

Pyth is currently available on the following cosmwasm chains:

### Stable

| Network   | Contract address                             |
| --------- | -------------------------------------------- |
| Injective Mainnet | [`inj12j43nf2f0qumnt2zrrmpvnsqgzndxefujlvr08`](https://explorer.injective.network/contract/inj12j43nf2f0qumnt2zrrmpvnsqgzndxefujlvr08/) |
| Osmosis Mainnet | [`osmo13ge29x4e2s63a8ytz2px8gurtyznmue4a69n5275692v3qn3ks8q7cwck7`](https://www.mintscan.io/osmosis/wasm/contract/osmo13ge29x4e2s63a8ytz2px8gurtyznmue4a69n5275692v3qn3ks8q7cwck7) |
| Neutron Mainnet | [`neutron1m2emc93m9gpwgsrsf2vylv9xvgqh654630v7dfrhrkmr5slly53spg85wv`](https://www.mintscan.io/neutron/wasm/contract/neutron1m2emc93m9gpwgsrsf2vylv9xvgqh654630v7dfrhrkmr5slly53spg85wv) |
| -------------- | -------------------------------------------------------------------- |
| Injective      | [`inj18hckkzqf47mdhd734g6papk6wj20y24rm43sk9`](https://testnet.explorer.injective.network/contract/inj18hckkzqf47mdhd734g6papk6wj20y24rm43sk9/)                         |
| Osmosis Test 5 | [`osmo1hpdzqku55lmfmptpyj6wdlugqs5etr6teqf7r4yqjjrxjznjhtuqqu5kdh`](https://testnet.mintscan.io/osmosis-testnet/wasm/contract/osmo1hpdzqku55lmfmptpyj6wdlugqs5etr6teqf7r4yqjjrxjznjhtuqqu5kdh)    |
| Sei Atlantic 2 | [`sei1w2rxq6eckak47s25crxlhmq96fzjwdtjgdwavn56ggc0qvxvw7rqczxyfy`](https://www.seiscan.app/testnet/contracts/sei1w2rxq6eckak47s25crxlhmq96fzjwdtjgdwavn56ggc0qvxvw7rqczxyfy)    |
| Neutron Pion 1 | `neutron1f86ct5az9qpz2hqfd5uxru02px2a3tz5zkw7hugd7acqq496dcms22ehpy` |
| Juno           | [`juno1eacsrua27njc35pxz37y97gmcjs899t59f8pf0rkejjyvtmhws5q6lxsdd`](https://testnet.ping.pub/juno/account/juno1eacsrua27njc35pxz37y97gmcjs899t59f8pf0rkejjyvtmhws5q6lxsdd)    |

### Edge

| Network        | Contract address                                                     |
| -------------- | -------------------------------------------------------------------- |
| Injective      | [`inj18rlflp3735h25jmjx97d22c72sxk260amdjxlu`](https://testnet.explorer.injective.network/contract/inj18rlflp3735h25jmjx97d22c72sxk260amdjxlu/)                         |
| Osmosis Test 5 | [`osmo1lltupx02sj99suakmuk4sr4ppqf34ajedaxut3ukjwkv6469erwqtpg9t3`](https://testnet.mintscan.io/osmosis-testnet/wasm/contract/osmo1lltupx02sj99suakmuk4sr4ppqf34ajedaxut3ukjwkv6469erwqtpg9t3)    |
| Sei Atlantic 2 | [`sei1kpntez76v38yuxhhaaahdmvjxnr5tkr8tq077smefs7uw70rj5yqw2aewy`](https://www.seiscan.app/testnet/contracts/sei1kpntez76v38yuxhhaaahdmvjxnr5tkr8tq077smefs7uw70rj5yqw2aewy)    |
| Neutron Pion 1 | `neutron1xxmcu6wxgawjlajx8jalyk9cxsudnygjg0tvjesfyurh4utvtpes5wmpjp` |
| Juno           | [`juno1h93q9kwlnfml2gum4zj54al9w4jdmuhtzrh6vhycnemsqlqv9l9snnznxs`](https://testnet.ping.pub/juno/account/juno1h93q9kwlnfml2gum4zj54al9w4jdmuhtzrh6vhycnemsqlqv9l9snnznxs)    |

## Price Feed IDs

The price feed IDs for stable and edge feeds are different and can be found here.

- [List of stable ids](https://pyth.network/developers/price-feed-ids#cosmwasm-stable)
- [List of edge ids](https://pyth.network/developers/price-feed-ids#cosmwasm-edge)
