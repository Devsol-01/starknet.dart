# starknet.dart

The goal of this SDK is to be able to interact with Starknet smart contracts in a type-safe way.

You can also call the JSON-RPC endpoint exposed by the Starknet full nodes (see the [specs](https://github.com/starkware-libs/starknet-specs)).

📚 [docs](https://pub.dev/packages/starknet)

💬 [telegram chat](https://t.me/+CWezjfLIRYc0MDY0)

## Motivation

Starknet is a revolution in the web3 world: it allows to [scale Ethereum](https://docs.ethhub.io/ethereum-roadmap/layer-2-scaling/zk-rollups/) and offers the best possible UX thanks to unique features like [account abstraction](https://www.argent.xyz/blog/wtf-is-account-abstraction/) or [session keys](https://github.com/dontpanicdao/starknet-burner).

But web3 mainstream adoption won't happen unless decentralized applications go to mobile.

That's why it's a priority to **build the best possible Starknet SDK for dart applications**, thus unlocking the era of Flutter mobile apps on Starknet.

## Roadmap

You can follow the progress of the project directly on the [kanban](https://github.com/users/gabsn/projects/1).

## Contributing

If you want to contribute to this project or have any suggestion, please check out our [Contributor Guide](CONTRIBUTING.md).

## Dev Guide

### Initial Setup

1. Install python deps. Make sure to select the python interpreter from the local .venv created by poetry if you're using VS Code.

```sh
poetry install
```

If you have an error about gmp install it like this :

```sh
brew install gmp
```

2. Run devnet in one terminal

```sh
poetry run devnet start
```

3. Setup devnet by deploying contracts

```sh
poetry run devnet setup
```

You can also deploy contracts one by one:

```sh
poetry run deploy balance
```

4. Interact with deployed contracts:

```sh
poetry run interact get_balance
poetry run interact increase_balance 10
```

### Run Tests

You can run the tests with the following command:

```
dart test
```

To run the tests on **devnet** use the following command:

```
NETWORK=devnet dart test -t integration
```

### Release a new version to pub.dev

You simply need to create a PR where you:

1. Bump the package version
2. Add an entry to the `CHANGELOG`

Make sure it passes all the CI tests, then merge it to release a new version of the package.

### Generate freezed model classes

To avoid writing too much boilerplate, we use the [freezed](https://github.com/rrousselGit/freezed) library to automatically generate serializer logic.

You can run the following command to generate those classes:

```
dart run build_runner build
```

Alternatively, you can hit `Cmd + Shift + B` in vscode.

### Generate docs

To generate docs, run:

```
dart doc .
```

For more advanced features, check out the [dartdoc package](https://pub.dev/packages/dartdoc).

### Compile cairo contracts

```sh
protostar build
```

You can see compiled contracts in the `contracts/build` folder.
