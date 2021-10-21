**Note: This repository is archived and no longer maintained. Refer to [this tutorial](https://docs.substrate.io/tutorials/v3/proof-of-existence/)
to learn how to build a proof of existence dApp.**

# Substrate Proof of Existence Module

This is a simple Substrate runtime module to store online distributed [proof of existence](https://www.proofofexistence.com/) for any file.

## Purpose

This module enables users submit a proof of existence for a file. This proof of existence may also be used as a soft measure of ownership.

Files are not directly uploaded to the blockchain. Instead, a [file digest](https://en.wikipedia.org/wiki/File_verification) is generated, and the resulting digest is stored on chain with the time of upload and the user who made the claim.

Anyone who has the source file can also generate the same digest and check the proof of existence on-chain.

## Dependencies

### Traits

This module depends on an implementation of the `Currency` trait. This can be done by the SRML Balances module.

### Modules

This module depends on the SRML Timestamp module.

## Installation

### Runtime `Cargo.toml`

To add this module to your runtime, simply include the following to your runtime's `Cargo.toml` file:

```rust
[dependencies.poe]
default_features = false
package = 'proof-of-existence'
git = 'https://github.com/substrate-developer-hub/substrate-proof-of-existence.git'
```

and update your runtime's `std` feature to include this module:

```rust
std = [
    ...
    'poe/std',
]
```

### Runtime `lib.rs`

You should implement it's trait like so:

```rust
impl poe::Trait for Runtime {
	type Currency = Balances;
	type Event = Event;
}
```

and include it in your `construct_runtime!` macro:

```rust
POE: poe::{Module, Call, Storage, Event<T>},
```

### Genesis Configuration

This template module does not have any genesis configuration.

## Reference Docs

You can view the reference docs for this module by running:

```
cargo doc --open
```
