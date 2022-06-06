---
description: Consume Pyth Network prices in applications on BNB Application Sidechains
---

# Deployment
If, as is highly likely, your BAS chain doesn't already have a deployment of Pyth, you will need to deploy the `Pyth2Wormhole` receiver contracts yourself. This is easy to do and will enable contracts deployed on your BAS chain to consume Pyth price feeds from the `PythUpgradable` contract.

To deploy the `Pyth2Wormhole` receiver contracts to your BAS chain:
- Clone the [pyth2wormhole repo](https://github.com/pyth-network/pyth2wormhole).
- Add your BAS network details to the [Truffle Networks configuration file](https://github.com/pyth-network/pyth2wormhole/blob/main/ethereum/truffle-config.js). An example stanza:
    ```json
    my_bas_testnet: {
        provider: () => new HDWalletProvider(
            process.env.MNEMONIC,
            "https://YOUR_BAS_RPC_ENDPOINT:8545"
        ),
        confirmations: 10,
        networkCheckTimeout: 1000000,
        timeoutBlocks: 1000,
        skipDryRun: true,
    }
    ```
 - Prepare a `.env.prod.my_bas_testnet` environment file in the `pyth2wormhole/ethereum` directory:
    ```
    # The truffle network name of your BAS chain, defined in the configuration earlier
    MIGRATIONS_NETWORK=my_bas_testnet

    # Keep these values the same
    MIGRATIONS_DIR=./migrations/prod-receiver    
    PYTH_TO_WORMHOLE_CHAIN_ID=0x1
    PYTH_TO_WORMHOLE_EMITTER=0xf346195ac02f37d60d4db8ffa6ef74cb1be3550047543a4a9ee9acf4d78697b0
    ```
 - Now run the Truffle migrations inside [`pyth2wormhole/migrations/prod-receiver`](https://github.com/pyth-network/pyth2wormhole/tree/main/ethereum/migrations/prod-receiver) using the instructions [here](https://github.com/pyth-network/pyth2wormhole/blob/main/ethereum/Deploying.md). Make sure you are deploying using the right environment file and to the correct network.
 - You can verify the contracts have been deployed successfully using the example [here](https://github.com/pyth-network/pyth2wormhole/blob/main/ethereum/Deploying.md#testing).

# Usage
After the pyth2wormhole contracts have been deployed to your BAS chain, please refer to the [Pyth on EVM-based chains documentation](evm.md) for how to consume price feeds.
