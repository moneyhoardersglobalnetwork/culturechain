# The Culture Chain

![](https://cms.polkadot.network/content/images/2021/06/1-xPcVR_fkITd0ssKBvJ3GMw.png)

[![StackExchange](https://img.shields.io/badge/StackExchange-Community%20&%20Support-222222?logo=stackexchange)](https://substrate.stackexchange.com/)

The Polkadot SDK repository provides all the resources needed to start building on the Polkadot network, a multi-chain
blockchain platform that enables different blockchains to interoperate and share information in a secure and scalable
way. The Polkadot SDK comprises three main pieces of software:



## [Substrate](./substrate/)
 [![SubstrateRustDocs](https://img.shields.io/badge/Rust_Docs-Substrate-24CC85?logo=rust)](https://paritytech.github.io/polkadot-sdk/master/polkadot_sdk_docs/polkadot_sdk/substrate/index.html)
 [![Substrate-license](https://img.shields.io/badge/License-GPL3%2FApache2.0-blue)](./substrate/README.md#LICENSE)

Substrate is the primary blockchain SDK used by developers to create the parachains that make up the Polkadot network.
Additionally, it allows for the development of self-sovereign blockchains that operate completely independently of
Polkadot.

## Releases

> [!NOTE]  
> Our release process is still Work-In-Progress and may not yet reflect the aspired outline here.

The Polkadot-SDK has two release channels: `stable` and `nightly`. Production software is advised to only use `stable`.
`nightly` is meant for tinkerers to try out the latest features. The detailed release process is described in
[RELEASE.md](docs/RELEASE.md).

### Stable

`stable` releases have a support duration of **three months**. In this period, the release will not have any breaking
changes. It will receive bug fixes, security fixes, performance fixes and new non-breaking features on a **two week**
cadence.

### Nightly

`nightly` releases are released every night from the `master` branch, potentially with breaking changes. They have
pre-release version numbers in the format `major.0.0-nightlyYYMMDD`.

## Upstream Dependencies

Below are the primary upstream dependencies utilized in this project:

- [`parity-scale-codec`](https://crates.io/crates/parity-scale-codec)
- [`parity-db`](https://crates.io/crates/parity-db)
- [`parity-common`](https://github.com/paritytech/parity-common)
- [`trie`](https://github.com/paritytech/trie)

## Security

The security policy and procedures can be found in [docs/contributor/SECURITY.md](./docs/contributor/SECURITY.md).

## Contributing & Code of Conduct

Ensure you follow our [contribution guidelines](./docs/contributor/CONTRIBUTING.md). In every interaction and
contribution, this project adheres to the [Contributor Covenant Code of Conduct](./docs/contributor/CODE_OF_CONDUCT.md).

## Additional Resources

- For monitoring upcoming changes and current proposals related to the technical implementation of the Polkadot network,
  visit the [`Requests for Comment (RFC)`](https://github.com/polkadot-fellows/RFCs) repository. While it's maintained
  by the Polkadot Fellowship, the RFC process welcomes contributions from everyone.
 
 //recompile the runtime by running the following command
cargo build --release --package culturechain-runtime

./target/release/culturechain build-spec --disable-default-bootnode --chain local > customSpec.json

./target/release/culturechain build-spec --chain=customSpec.json --raw --disable-default-bootnode > mawulisa.json

./target/release/culturechain build-spec --chain=customSpec.json --raw --disable-default-bootnode > culturechain.json


## Run RoHo Devnet

  ./target/release/culturechain purge-chain --base-path /tmp/alice --chain local

  ./target/release/culturechain \
--base-path /tmp/alice \
--chain ./roho.json \
--chain dev \
--alice \
--port 30333 \
--rpc-port 9945 \
--node-key 0000000000000000000000000000000000000000000000000000000000000001 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator

./target/release/culturechain purge-chain --base-path /tmp/bob --chain local -y

./target/release/culturechain \
--base-path /tmp/bob \
--chain ./roho.json \
--chain local \
--bob \
--port 30334 \
--rpc-port 9946 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp

./target/release/culturechain purge-chain --base-path /tmp/charlie --chain local -y

./target/release/culturechain \
--base-path /tmp/charlie \
--chain ./roho.json \
--chain local \
--charlie \
--port 30335 \
--rpc-port 9947 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp


./target/release/culturechain \
  --base-path /tmp/node01 \
  --chain ./roho.json \
  --port 30333 \
  --rpc-port 9945 \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode01 \
  --password-interactive


## Run Mawu-Lisa Testnet
./target/release/culturechain \
--base-path /tmp/alice2 \
--chain ./mawulisa.json \
--alice \
--port 30333 \
--rpc-port 9945 \
--node-key 0000000000000000000000000000000000000000000000000000000000000001 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator

  ./target/release/culturechain \
--base-path /tmp/bob2 \
--chain ./mawulisa.json \
--bob \
--port 30339 \
--rpc-port 9949 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp

./target/release/culturechain \
--base-path /tmp/charlie2 \
--chain ./mawulisa.json \
--charlie \
--port 30339 \
--rpc-port 9949 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp

## Run Culture Chain Mainnet
./target/release/culturechain \
--base-path /tmp/alice2 \
--chain ./mawulisa.json \
--alice \
--port 30333 \
--rpc-port 9945 \
--node-key 0000000000000000000000000000000000000000000000000000000000000001 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator

  ./target/release/culturechain \
--base-path /tmp/bob2 \
--chain ./mawulisa.json \
--bob \
--port 30339 \
--rpc-port 9949 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp

./target/release/culturechain \
--base-path /tmp/charlie2 \
--chain ./mawulisa.json \
--charlie \
--port 30339 \
--rpc-port 9949 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp