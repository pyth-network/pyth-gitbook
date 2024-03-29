---
description: Consume Pyth Network prices in EVM applications
---

# Pyth on EVM

On-chain EVM programs can use the [Solidity SDK](https://github.com/pyth-network/pyth-sdk-solidity) to read Pyth prices. The off-chain portion of the application can use [pyth-evm-js](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/ethereum/sdk/js) to generate price update transactions. This repository's [Quickstart](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/ethereum/sdk/js#quickstart) includes an example of both the on- and off-chain code necessary to integrate with Pyth.

## Example - Oracle Swap 

[Oracle Swap](https://github.com/pyth-network/pyth-crosschain/tree/main/target_chains/ethereum/examples/oracle_swap) is an end-to-end example application that uses Pyth Network.
This application is an AMM that allows users to swap two assets at the Pyth-provided exchange rate. This application contains both the contract, and the frontend to interact with the contract. 

## EVM price pusher

[Pyth EVM price pusher](https://github.com/pyth-network/pyth-crosschain/tree/main/price_pusher)
is a service that regularly pushes price updates to the on-chain Pyth contract.
Protocols can run this service to push regular updates to the on-chain Pyth price based on various conditions, such as a minimum update frequency, or a price change threshold.
This service is useful for protocols that already depend on regular push updates and want to simplify  migrating to Pyth.
Please see the github readme for additional information on this service.

In addition, you can find an in-depth explanation from one of our contributors, Ali:
[How to Build with Pyth Data on EVM Chains (with Pusher): Pyth Tutorials](https://youtu.be/yhmo81JOH10)

## Networks

Pyth is currently available on the following EVM-based chains:


### Mainnet

| Network        | Contract address                             |
| -------------- | -------------------------------------------- |
| Avalanche      | [`0x4305FB66699C3B2702D4d05CF36551390A4c69C6`](https://snowtrace.io/address/0x4305fb66699c3b2702d4d05cf36551390a4c69c6) |
| Fantom         | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://ftmscan.com/address/0xff1a0f4744e8582df1ae09d5611b887b6a12925c) |
| Polygon        | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://polygonscan.com/address/0xff1a0f4744e8582df1ae09d5611b887b6a12925c) |
| BNB            | [`0x4D7E825f80bDf85e913E0DD2A2D54927e9dE1594`](https://bscscan.com/address/0x4d7e825f80bdf85e913e0dd2a2d54927e9de1594) |
| Ethereum       | [`0x4305FB66699C3B2702D4d05CF36551390A4c69C6`](https://etherscan.io/address/0x4305fb66699c3b2702d4d05cf36551390a4c69c6) |
| Optimism       | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://optimistic.etherscan.io/address/0xff1a0f4744e8582df1ae09d5611b887b6a12925c) |
| Aurora         | [`0xF89C7b475821EC3fDC2dC8099032c05c6c0c9AB9`](https://explorer.aurora.dev/address/0xF89C7b475821EC3fDC2dC8099032c05c6c0c9AB9) |
| Arbitrum       | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://arbiscan.io/address/0xff1a0f4744e8582df1ae09d5611b887b6a12925c) |
| Celo           | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://celoscan.io/address/0xff1a0f4744e8582df1ae09d5611b887b6a12925c) |
| KCC            | [`0xE0d0e68297772Dd5a1f1D99897c581E2082dbA5B`](https://explorer.kcc.io/en/address/0xe0d0e68297772dd5a1f1d99897c581e2082dba5b) |
| Cronos         | [`0xE0d0e68297772Dd5a1f1D99897c581E2082dbA5B`](https://cronoscan.com/address/0xe0d0e68297772dd5a1f1d99897c581e2082dba5b) |
| zkSync Era     | [`0xf087c864AEccFb6A2Bf1Af6A0382B0d0f6c5D834`](https://explorer.zksync.io/address/0xf087c864AEccFb6A2Bf1Af6A0382B0d0f6c5D834) |
| EVMOS          | [`0x354bF866A4B006C9AF9d9e06d9364217A8616E12`](https://www.mintscan.io/evmos/evm/contract/0x354bF866A4B006C9AF9d9e06d9364217A8616E12) |
| Polygon zkEVM  | [`0xC5E56d6b40F3e3B5fbfa266bCd35C37426537c65`](https://zkevm.polygonscan.com/address/0xc5e56d6b40f3e3b5fbfa266bcd35c37426537c65) |
| Meter          | [`0xbFe3f445653f2136b2FD1e6DdDb5676392E3AF16`](https://scan.meter.io/address/0xbfe3f445653f2136b2fd1e6dddb5676392e3af16) |
| Conflux eSpace | [`0xe9d69CdD6Fe41e7B621B4A688C5D1a68cB5c8ADc`](https://evm.confluxscan.io/address/0xe9d69cdd6fe41e7b621b4a688c5d1a68cb5c8adc) |
| Canto          | [`0x98046Bd286715D3B0BC227Dd7a956b83D8978603`](https://www.mintscan.io/canto/evm/contract/0x98046Bd286715D3B0BC227Dd7a956b83D8978603) |
| Kava           | [`0xA2aa501b19aff244D90cc15a4Cf739D2725B5729`](https://explorer.kava.io/address/0xA2aa501b19aff244D90cc15a4Cf739D2725B5729) |
| Gnosis         | [`0x2880aB155794e7179c9eE2e38200202908C17B43`](https://gnosisscan.io/address/0x2880ab155794e7179c9ee2e38200202908c17b43) |
| WEMIX          | ['0xA2aa501b19aff244D90cc15a4Cf739D2725B5729`](https://explorer.wemix.com/address/0xA2aa501b19aff244D90cc15a4Cf739D2725B5729) |

### Testnet

| Network                     | Contract address                             |
| --------------------------- | -------------------------------------------- |
| Goerli (Ethereum testnet)   | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://goerli.etherscan.io/address/0xff1a0f4744e8582DF1aE09D5611b887B6a12925C) |
| Fuji (Avalanche testnet)    | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://testnet.snowtrace.io/address/0xff1a0f4744e8582DF1aE09D5611b887B6a12925C) |
| Fantom testnet              | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://testnet.ftmscan.com/address/0xff1a0f4744e8582df1ae09d5611b887b6a12925c) |
| Mumbai (Polygon testnet)    | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://mumbai.polygonscan.com/address/0xff1a0f4744e8582DF1aE09D5611b887B6a12925C) |
| BNB testnet                 | [`0xd7308b14BF4008e7C7196eC35610B1427C5702EA`](https://testnet.bscscan.com/address/0xd7308b14BF4008e7C7196eC35610B1427C5702EA) |
| Aurora testnet              | [`0x4305FB66699C3B2702D4d05CF36551390A4c69C6`](https://explorer.testnet.aurora.dev/address/0x4305FB66699C3B2702D4d05CF36551390A4c69C6) |
| Optimism Goerli (testnet)   | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://goerli-optimism.etherscan.io/address/0xff1a0f4744e8582df1ae09d5611b887b6a12925c) |
| Celo Alfajores (testnet)    | [`0xff1a0f4744e8582DF1aE09D5611b887B6a12925C`](https://explorer.celo.org/alfajores/address/0xff1a0f4744e8582DF1aE09D5611b887B6a12925C) |
| KCC testnet                 | [`0x15D35b8985e350f783fe3d95401401E194ff1E6f`](https://scan-testnet.kcc.network/address/0x15D35b8985e350f783fe3d95401401E194ff1E6f) |
| Cronos testnet              | [`0xBAEA4A1A2Eaa4E9bb78f2303C213Da152933170E`](https://cronos.org/explorer/testnet3/address/0xBAEA4A1A2Eaa4E9bb78f2303C213Da152933170E) |
| Arbitrum Goerli (testnet)   | [`0x939C0e902FF5B3F7BA666Cc8F6aC75EE76d3f900`](https://goerli.arbiscan.io/address/0x939C0e902FF5B3F7BA666Cc8F6aC75EE76d3f900) |
| zkSync Era Goerli (testnet) | [`0xC38B1dd611889Abc95d4E0a472A667c3671c08DE`](https://goerli.explorer.zksync.io/address/0xC38B1dd611889Abc95d4E0a472A667c3671c08DE) |
| Base Goerli (testnet)       | [`0x5955C1478F0dAD753C7E2B4dD1b4bC530C64749f`](https://goerli.basescan.org/address/0x5955c1478f0dad753c7e2b4dd1b4bc530c64749f) |
| Shimmer testnet             | [`0xA2aa501b19aff244D90cc15a4Cf739D2725B5729`](https://explorer.evm.testnet.shimmer.network/address/0xA2aa501b19aff244D90cc15a4Cf739D2725B5729) |
| Chiado (Gnosis testnet)     | [`0xdDAf6D29b8bc81c1F0798a5e4c264ae89c16a72B`](https://blockscout.com/gnosis/chiado/address/0xdDAf6D29b8bc81c1F0798a5e4c264ae89c16a72B) |
| EVMOS testnet               | [`0x354bF866A4B006C9AF9d9e06d9364217A8616E12`](https://evm.evmos.dev/address/0x354bF866A4B006C9AF9d9e06d9364217A8616E12) |
| Neon devnet                 | [`0x2FF312f50689ad279ABb164dB255Eb568733BD6c`](https://neonscan.org/address/0x2FF312f50689ad279ABb164dB255Eb568733BD6c) |
| Polygon zkEVM testnet       | [`0xd54bf1758b1C932F86B178F8b1D5d1A7e2F62C2E`](https://testnet-zkevm.polygonscan.com/address/0xd54bf1758b1c932f86b178f8b1d5d1a7e2f62c2e) |
| Canto testnet               | [`0xA2aa501b19aff244D90cc15a4Cf739D2725B5729`](https://testnet-explorer.canto.neobase.one/address/0xA2aa501b19aff244D90cc15a4Cf739D2725B5729) |
| Meter testnet               | [`0x5fF5B9039FbD8256864A4460B7EA77093A65B1b5`](https://scan-warringstakes.meter.io/address/0x5ff5b9039fbd8256864a4460b7ea77093a65b1b5) |
| Mantle testnet              | [`0xA2aa501b19aff244D90cc15a4Cf739D2725B5729`](https://explorer.testnet.mantle.xyz/address/0xA2aa501b19aff244D90cc15a4Cf739D2725B5729) |
| Conflux eSpace testnet      | [`0xA2aa501b19aff244D90cc15a4Cf739D2725B5729`](https://evmtestnet.confluxscan.io/address/0xa2aa501b19aff244d90cc15a4cf739d2725b5729) |
| Kava testnet                | [`0x98046Bd286715D3B0BC227Dd7a956b83D8978603`](https://explorer.testnet.kava.io/address/0x98046Bd286715D3B0BC227Dd7a956b83D8978603) |
| WEMIX testnet              | [`0xA2aa501b19aff244D90cc15a4Cf739D2725B5729`](https://explorer.test.wemix.com/address/0xA2aa501b19aff244D90cc15a4Cf739D2725B5729) |


## Price Feed IDs

The price feed IDs for EVM chains differs depending on whether they are a mainnet or testnet (see above):
* [List of mainnet ids](https://pyth.network/developers/price-feed-ids#pyth-evm-mainnet)
* [List of testnet ids](https://pyth.network/developers/price-feed-ids#pyth-evm-testnet)
