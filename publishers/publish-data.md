# Getting started with publishing via pyth-client

{% hint style="info" %}
To publish data you will need to be permissioned: please reach out to the Pyth Data Association on [Discord](https://discord.gg/Ff2XDydUhu) or [Telegram](https://t.me/Pyth_Network) to get set up.
{% endhint %}

The pyth-client repo consists of two command-line administration tools (pyth & pyth_admin) and a json/websocket-based server (pythd).

You can integrate with the pythd server via json/websockets. See `pctest/test_publish.py` for an example.

Before doing this you need to setup a *key-store* directory. A key-store is a collection of cryptographic keys for interacting with the solana block-chain. This can be done via the pyth command-line tool.  First, build the project by following the instructions in the README.md file and cd to the build directory, then run the following:


```
KDIR=$HOME/.pythd
./pyth init_key -k $KDIR

```

You can replace `$KDIR` with a directory of your choice.

This creates the directory (if it didn't already exist) and creates a key-pair file containing the identifier you're going to use to publish to the block-chain: `$KDIR/publish_key_pair.json`.

Please extract the public key from this key-pair and send it to the administrator so it can be permissioned for your symbols of interest. The public key can be extracted as follows:

```
solana-keygen pubkey $KDIR/publish_key_pair.json
```

This will output the public key in base58 encoding and will look something like:

```
5rYvdyWAunZgD2EC1aKo7hQbutUUnkt7bBFM6xNq2z7Z
```

Once permissioned, you need two additional public keys in the key-store. The id of the mapping-account that contains the directory listing of the on-chain symbols and the id of the on-chain oracle program that you use to publish prices.  Mapping and program accounts are maintained in two separate environments: devnet and forthcoming mainnet-beta.

Use the init_key_store.sh script to initialize these account keys:

```
KENV=devnet  # or testnet, mainnet

# initialize keys for solana devnet
../pctest/init_key_store.sh $KENV $KDIR

```

This creates two files: `$KDIR/mapping_key.json` and `$KDIR/program_key.json`.

Once permissioned, you can test your setup by running the test_publish.py example program against pythd for publishing and subscribing to a test symbol.  To test publishing on devnet you first need to run an instance of the pythd server:


```
RHOST=api.devnet.solana.com
./pythd -k $KDIR -r $RHOST -x
```

Where RHOST is the location of the Solana validator instance.

Run the test_publish.py example program on the same host to connect to the pythd server:

```
../pctest/test_publish.py

```


## Running the dashboard

The pythd server also exports a dashboard web page for watching the ticking pyth prices.  The public key you create above does not need publish-permission to watch the ticking pyth prices.  To activate the dashboard page include an additional `-w` argument to pythd pointing at the html/javscript code directory:

```
./pythd -k $KDIR -r $RHOST -w ../dashboard
```

Connect to the dashboard via http://localhost:8910.
