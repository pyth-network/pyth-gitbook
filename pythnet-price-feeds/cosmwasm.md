---
description: Consume Pyth Network prices in applications on Cosmwasm
---

# Pyth on Cosmwasm

Cosmwasm contracts can update and fetch the Pyth prices using the Pyth Cosmwasm Contract, deployed on their network. The documented source code can be found [here](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/cosmwasm/contracts/pyth).

## Updating Price Feeds

The mechanism by which price feeds are updated on Cosmwasm is explained [here](./pythnet-price-feeds.md). The [pyth-common-js](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/cosmwasm/sdk/js) can be used to fetch the latest price feed data which then can be passed to the `ExecuteMsg` on-chain function.

## Examples

- [Minimal on-chain contract](https://github.com/pyth-network/pyth-crosschain/blob/main/target_chains/cosmwasm/examples/cw-contract) which queries the Pyth contract.

## Networks

Pyth is currently available on the following cosmwasm chains:

### Mainnet

| Network   | Contract address                             |
| --------- | -------------------------------------------- |
| Injective | `inj12j43nf2f0qumnt2zrrmpvnsqgzndxefujlvr08` |

### Testnet

| Network        | Contract address                                                     |
| -------------- | -------------------------------------------------------------------- |
| Injective      | `inj1yzx0wdn6t7xrjdpgztnrraq57nw2zxhstr97xw`                         |
| Sei Atlantic 2 | `sei1977nnu5jqatteqgve8tx7nzu9y7eh6cvq0e4g6xjx8tf5wm4nkmsfljunh`     |
| Osmosis Test 4 | `osmo1xws8v2yv50v0spn90yr9fe9zx8zxfppl3syn38zw59npvp8dd70sutnvsm`    |
| Osmosis Test 5 | `osmo12u2vqdecdte84kg6c3d40nwzjsya59hsj048n687m9q3t6wdmqgsq6zrlx`    |
| Neutron Pion 1 | `neutron1zpn7yhxqx2f0c6cpmp3fr42yafupz9elglvgdss2300c847ph0hsgurhlj` |
| Juno           | `juno1ygyhu0zn69zm0354nzpd7zrp5xs9vpkqcuk7kfneyghrpa87msmqeskxqa`    |

## Price Feed IDs

The price feed IDs for cosmwasm chains are the same for both mainnet and testnet.

- [List of price feed ids](https://pyth.network/developers/price-feed-ids#cosmwasm-mainnet)
