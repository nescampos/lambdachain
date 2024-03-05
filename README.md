# Lambda Chain

An Enterprise-grade and permissionless blockchain built on Polkadot, built with [Substrate SDK](https://github.com/substrate-developer-hub/substrate-node-template)

The focus of Lambda Chain is to be a network for the financial industry (banks, fintech, and more) for interoperable payments, streaming payments, and off-chain payment channels, among others.

## Features / pallets

### Escrow
This feature allows you to create escrows, pay, dispute funds (with an intermediary), release funds, close, and more.
- Pay (create escrow)
```
pay(origin,recipient,asset,amount,remark)
```

- Release funds (finish the payment)
```
release(origin,to)
```

- Cancel a payment
```
cancel(origin,creator)
```

- Resolve dispute
```
resolve_payment(origin,from,recipient,recipient_share)
```

- Request refund
```
request_refund(origin, recipient)
```

- Dispute refund
```
dispute_refund(origin, creator)
```

- Request payment
```
request_payment(origin,from,asset, amount)
```

- Accept and pay
```
accept_and_pay(origin, to)
```


### Payment Streaming
This feature supports creating streams i.e. ongoing payments. Once a stream is opened, on every block a specified amount of funds will be transferred from the origin account to the given target account, until the stream is closed.

- Open stream
```
open_stream(origin, target, spend_rate)
```

- Close stream
```
close_stream(origin, streamIndex)
```

### Payment Channel
Coming soon.

### ISO 20022 compatibility
Coming soon.

### Gasless experience
Coming soon.

### Sidechains
Coming soon.


## Getting Started

Depending on your operating system and Rust version, there might be additional packages required to compile this template.
Check the [Install](https://docs.substrate.io/install/) instructions for your platform for the most common dependencies.
Alternatively, you can use one of the [alternative installation](#alternatives-installations) options.

### Build

Use the following command to build the node without launching it:

```sh
cargo build --release
```


### Single-Node Lambda Chain

The following command starts a single-node development chain that doesn't persist state:

```sh
./target/release/lambdachain --dev
```

To purge the Lambda Chain's state, run the following command:

```sh
./target/release/lambdachain purge-chain --dev
```

To start the Lambda chain with detailed logging, run the following command:

```sh
RUST_BACKTRACE=1 ./target/release/lambdachain -ldebug --dev
```

Development chains:

- Maintain state in a `tmp` folder while the node is running.
- Use the **Alice** and **Bob** accounts as default validator authorities.
- Use the **Alice** account as the default `sudo` account.
- Are preconfigured with a genesis state (`/node/src/chain_spec.rs`) that includes several prefunded development accounts.


To persist chain state between runs, specify a base path by running a command similar to the following:

```sh
// Create a folder to use as the db base path
$ mkdir my-chain-state

// Use of that folder to store the chain state
$ ./target/release/lambdachain --dev --base-path ./lambda-state/

// Check the folder structure created inside the base path after running the chain
$ ls ./lambda-state
chains
$ ls ./lambda-state/chains/
dev
$ ls ./lambda-state/chains/dev
db keystore network
```

### Connect with Polkadot-JS Apps Front-End

After you start the Lambda Chain locally, you can interact with it using the hosted version of the [Polkadot/Substrate Portal](https://polkadot.js.org/apps/#/explorer?rpc=ws://localhost:9944) front-end by connecting to the local node endpoint.

### Multi-Node Local Testnet

If you want to see the multi-node consensus algorithm in action, see [Simulate a network](https://docs.substrate.io/tutorials/build-a-blockchain/simulate-network/).

