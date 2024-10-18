# Specifications
The documentation will be shared here: https://defiralia.com/swap-defirealia/

# Getting Started
Defiraliacoin requires some dependencies to be built and deployed.

Dependencies required to build and deploy Defiraliacoin program:
- Rust 1.73.0 or higher
- Solana CLI 1.14.17
- Anchor 0.27.0

Dependencies required to run TypeScript tests:
- NodeJS 18.2.0 or higher
- Yarn 1.22.19

You can either install these dependencies in your OS manually or install Docker and use Dockerfile provided in this repository to start pre-configured container with all the dependencies. The second way is recommended because it's much simpler and less error-prone.

## Without Docker
Install dependencies mentioned above. Please check the links below to find out on how to install the dependencies:
- Rust: https://www.rust-lang.org/tools/install
- Solana CLI: https://docs.solana.com/cli/install-solana-cli-tools
- Anchor: https://www.anchor-lang.com/docs/installation
- NodeJS: https://nodejs.org/en/download/
- Yarn: https://yarnpkg.com/getting-started/install

# Commands
Execute below commands in the environment where you set up the dependencies mentioned above in Getting Started section - either in the Docker's container (if you used one) or directly in your OS if you deployed DefiraliaCoin there.

- Build DefiraliaCoin (compiles Rust code): `cargo build`
- Solve dependency conflict: `cargo update -p borsh@0.10.4 --precise 0.9.3`
- Install NPM dependencies (required to run tests in TypeScript): `yarn install`
- Start test Solana validator: `solana-test-validator`
- Run tests in Rust for DefiraliaCoin: `cargo test`

# Project Structure 
The project structure is based on the standard Anchor's template which is composed of contracts, tests, and deploy instructions. The template provides a great starting point for developers to quickly get up and running and deploying smart contracts on the Solana blockchain.

## Main contract files
Main contract files are placed in the `programs\DefiraliaToken` directory.

Besides `Cargo.toml` and `Xargo.toml` files used by Rust to build the code, there is also `src` directory with the actual source code of the contract. It contains the following files:
- `lib.rs` - the main contract file with exposed functions,
- `account.rs` - contains structures of accounts used in `lib.rs`,
- `context.rs` - contains structures of contexts used in `lib.rs`,
- `error.rs` - contains all errors used in `lib.rs` and `utils.rs`,
- `utils.rs` - contains helper structures and functions used in `lib.rs`.

The files include also Rust tests (more details in [Tests section](#tests) ).

```rust
crate DefiraliaCoin
  ├── mod account
  ├── mod context
  ├── mod error
  ├── mod DefiraliaCoin
  └── mod utils
```

## TypeScript Tests
TypeScript tests are placed in the `tests` directory. It contains the following files:
- `DefiraliaCoin.ts` file - integration tests for the contract (more details in [Tests section](#tests) ),
- `utils` directory - helper functions used in `DefiraliaCoin.ts` file.

There are also some files related to TypeScript tests placed at root level:
- `.env` file - contains environment variables used by the tests,
- `package.json` file - declares dependencies and scripts used by TypeScript to run tests,
- `tsconfig.json` file - contains compiler options used to compile TypeScript files with tests.

## Other files
There are also few other files like Prettier configuration or Anchor configuration files at the root level.

# Documentation
Execute the following command to generate code documentation: `cargo doc --open`

## Running tests
Use the following commands to run tests:
- Solve dependency conflict (temporary fix): `cargo update -p borsh@0.10.4 --precise 0.9.3`
- Rust tests: `cargo test`
