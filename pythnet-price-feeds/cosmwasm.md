---
description: Consume Pyth Network prices in applications on Cosmwasm
---

# Pyth on Cosmwasm

Cosmwasm contracts can update and fetch the Pyth prices using the Pyth Cosmwasm Contract, deployed on their network. The documented source code can be found [here](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/cosmwasm/contracts/pyth).

## Price Feeds
Pythnet price feeds uses an on-demand price update model, where users are responsible for posting price updates on-chain when needed. The latest price can be fetched from a price service, which is a permissionless centralised service. We recommend protocols to run their own price-service. 
Pythnet publishes prices for two kinds of feeds: 
1. Stable price feeds are the most reliable price feeds.
2. Edge price feeds comes with the latest and greatest features of Pyth price feeds as soon as they are available. 

Mainnet only supports the stable version of price feeds whereas testnet supports both. 

To learn more about the mechanism by which price feeds are updated on Cosmwasm you can follow this [link](./pythnet-price-feeds.md). The [pyth-common-js](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/cosmwasm/sdk/js) can be used to fetch the latest price feed data which then can be passed to the `ExecuteMsg` on-chain function.

### Price Service Public Endpoints
| Price feeds | url                             |
| ------- | ------------------------------- |
| stable | https://xc-mainnet.pyth.network |
| edge | https://xc-testnet.pyth.network |

```
# Example API call
$ curl https://xc-testnet.pyth.network/api/latest_vaas?ids[]=0xf9c0172ba10dfa4d19088d94f5bf61d3b54d5bd7483a322a982e1373ee8ea31b

# Example Response
["AQAAAAABALNY33VN+Pxh+vh02T9mAjCkNlug8K7qYTEPa+vU/hcSP+IGYDm75QCZ2oVdYdV45tXmsnAqnQwnybTt5QqOX8wBZG4AGAAAAAAAGqJ4OdZBsHdDwMtfaMUfjNMdLAdivsANxvzSVDPvGrW2AAAAAAMOaTIBUDJXSAADAAEAAQIABQCdHNsaXh40VtKXfuDT1wdlI58IpChVuVCP1HnhXG3E0f7s9VN3DZsQll+Ptkdx6T9WkKGC7cMr5KMjbgyqpuBYGgAAAAcxcTjgAAAAAAG6Nuf////4AAAABy+1l2gAAAAAAS3wagEAAAABAAAAAgAAAABkbgAYAAAAAGRuABQAAAAAZG4AEgAAAAcxWUAQAAAAAAEH63AAAAAAZG4AFGogZxwOP4yyGc4/RuWuCWpPL9+TbSvU2okl9wCH1R3YMAKUeVmHlykONjihcSwpveI2fQ7KeU93iyW1pHLxkt4AAAACoO+6gAAAAAAAmJaA////+AAAAAKgDbl4AAAAAACW+rcBAAAAAQAAAAIAAAAAZG4AGAAAAABkbgAXAAAAAGRuABQAAAACoOKsoQAAAAAAw+FuAAAAAGRuABco/gXScIxlcRgqfJ0f9FeiIbRl7fXqmvE3P5Vi0WuNFfnAFyuhDfpNGQiNlPW/YdO1TVvXSDoyKpguE3PujqMbAAACbg2tzH8AAAAAHz3sv/////gAAAJuPkE5QAAAAAAkkZ1wAQAAAAEAAAACAAAAAGRuABgAAAAAZG4AFwAAAABkbgAVAAACbg13O78AAAAAJKtrvwAAAABkbgAXizjbcA6LNGQOaB7Jpz6JYIvaKUFVR6Ik+WWFGStLnceUvOSu6I/fpbWNgQkL1rN4Rxf6bfhUGdnwRDO7PWFdXAAAAAAFAlNUAAAAAAAA9ED////4AAAAAAUHGlgAAAAAAAEesgEAAAABAAAAAgAAAABkbgAYAAAAAGRuABcAAAAAZG4AFAAAAAAFAlNUAAAAAAAA9EAAAAAAZG4AFztpo88HVkbF/YFItwW4EH5hoaJT1dioQ1Xctiiz8dEgMXdeHWiXEp6KhO66l1d4+1ABW4gDnpvBQLvYOWlKwK4AAAAAAGyBWAAAAAAAABOK////+AAAAAAAbHdcAAAAAAAAD4ABAAAAAQAAAAIAAAAAZG4AGAAAAABkbgAYAAAAAGRuABUAAAAAAGyBWAAAAAAAABOKAAAAAGRuABU="]

```

## Examples

- [Minimal on-chain contract](https://github.com/pyth-network/pyth-crosschain/blob/main/target_chains/cosmwasm/examples/cw-contract) which queries the Pyth contract.

## Networks

Pyth is currently available on the following cosmwasm chains:

### Mainnet (Stable)

| Network   | Contract address                             |
| --------- | -------------------------------------------- |
| Injective | `inj12j43nf2f0qumnt2zrrmpvnsqgzndxefujlvr08` |
| Osmosis | `osmo13ge29x4e2s63a8ytz2px8gurtyznmue4a69n5275692v3qn3ks8q7cwck7` |

### Testnet (Stable)

| Network        | Contract address                                                     |
| -------------- | -------------------------------------------------------------------- |
| Injective      | `inj18hckkzqf47mdhd734g6papk6wj20y24rm43sk9`                         |
| Osmosis Test 4 | `osmo1cg4vhqqknj4ad84m4l7duw6ll23dxwuu76yaw63lhw55k46nt8ysuen2xc`    |
| Osmosis Test 5 | `osmo1hpdzqku55lmfmptpyj6wdlugqs5etr6teqf7r4yqjjrxjznjhtuqqu5kdh`    |
| Neutron Pion 1 | `neutron1f86ct5az9qpz2hqfd5uxru02px2a3tz5zkw7hugd7acqq496dcms22ehpy` |
| Juno           | `juno1eacsrua27njc35pxz37y97gmcjs899t59f8pf0rkejjyvtmhws5q6lxsdd`    |

### Testnet (Edge)

| Network        | Contract address                                                     |
| -------------- | -------------------------------------------------------------------- |
| Injective      | `inj18rlflp3735h25jmjx97d22c72sxk260amdjxlu`                         |
| Osmosis Test 4 | `osmo1hj9wsf04y98e4979r9vknmv3ca76r2f06ztrwjgp96e9rkh5we4swntsp7`    |
| Osmosis Test 5 | `osmo1lltupx02sj99suakmuk4sr4ppqf34ajedaxut3ukjwkv6469erwqtpg9t3`    |
| Neutron Pion 1 | `neutron1xxmcu6wxgawjlajx8jalyk9cxsudnygjg0tvjesfyurh4utvtpes5wmpjp` |
| Juno           | `juno1h93q9kwlnfml2gum4zj54al9w4jdmuhtzrh6vhycnemsqlqv9l9snnznxs`    |

## Price Feed IDs

The price feed IDs for stable and edge feeds are different and can be found here.

- [List of stable ids](https://pyth.network/developers/price-feed-ids#cosmwasm-stable)
- [List of edge ids](https://pyth.network/developers/price-feed-ids#cosmwasm-edge)
