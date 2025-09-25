# Supporting Guide to Linera Protocol Repository


This guide is designed for technical developers (focusing on code structure, crates, modules, and examples) and non-technical/newcomers (who can focus on high-level concepts and overviews). We'll progress from basics to advanced components, helping you assimilate information step by step. Each section includes:

- **Overview**: What the section covers and its importance.
- **Key Files/Folders**: Clickable links to code files, or tree views for folders.
- **Learning Path**: Suggested order, with tips on connecting concepts.
- **Transitions**: Guidance on moving to the next section.

The structure covers setup, core crates, supporting crates, examples, advanced tools, and additional resources. Start at the beginning for a complete understanding.

## 1. Getting Started (Setup and Installation)
This section covers repository basics, installation, and contribution guidelines. Essential for setting up your environment and understanding the project.

### Key Concepts Covered
- Project overview, dependencies, build instructions, and how to contribute.

### Key Files
- [`README.md`](https://github.com/linera-io/linera-protocol/blob/main/README.md): High-level intro, quickstart, repo structure, and links to whitepaper/docs.
- [`INSTALL.md`](https://github.com/linera-io/linera-protocol/blob/main/INSTALL.md): Software requirements and setup.
- [`CONTRIBUTING.md`](https://github.com/linera-io/linera-protocol/blob/main/CONTRIBUTING.md): Guidelines for code contributions, issues, and PRs.
- [`Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/Cargo.toml): Workspace configuration for all crates.
- [`Cargo.lock`](https://github.com/linera-io/linera-protocol/blob/main/Cargo.lock): Dependency lockfile.
- [`rust-toolchain.toml`](https://github.com/linera-io/linera-protocol/blob/main/rust-toolchain.toml): Rust version specification.
- [`.github/`](https://github.com/linera-io/linera-protocol/tree/main/.github): Workflows for CI/CD (e.g., [`workflows/rust.yml`](https://github.com/linera-io/linera-protocol/blob/main/.github/workflows/rust.yml)).

### Learning Path
1. Read [`README.md`](https://github.com/linera-io/linera-protocol/blob/main/README.md) for the overall project and quickstart (e.g., running a local network).
2. Follow [`INSTALL.md`](https://github.com/linera-io/linera-protocol/blob/main/INSTALL.md) to install Rust and dependencies.
3. Review [`CONTRIBUTING.md`](https://github.com/linera-io/linera-protocol/blob/main/CONTRIBUTING.md) and check CI workflows in [`.github/`](https://github.com/linera-io/linera-protocol/tree/main/.github).
4. Examine [`Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/Cargo.toml) to see crate dependencies.

**Tips**: Run `cargo build` after setup to verify. Newcomers, focus on README; devs, note the monorepo setup.

**Transition**: With basics in place, dive into core crates for protocol fundamentals.

## 2. Core Crates (Protocol Fundamentals)
These foundational crates handle low-level logic like cryptography, data views, execution, chains, and storage. Start here to understand Linera's architecture.

### 2.1 linera-base
Base types, crypto, and utilities.

#### Key Files/Folders
- [`linera-base/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-base/Cargo.toml): Crate config.
- [`linera-base/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-base/src/lib.rs): Entry point.
- [`linera-base/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-base/src): Source dir with modules like abi.rs, chain_id.rs, crypto.rs, data_types.rs, doc_scalar.rs, identifiers.rs, ownership.rs, time.rs, unit_tests/.

### Learning Path
1. Start with [`lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-base/src/lib.rs) for exports.
2. Explore crypto and identifiers modules.

### 2.2 linera-version
Version management for binaries.

#### Key Files/Folders
- [`linera-version/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-version/Cargo.toml).
- [`linera-version/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-version/src/lib.rs): Main logic.

### Learning Path
- Read the single module for version handling.

### 2.3 linera-views and linera-views-derive
Data structures on key-value stores; derive macros.

#### Key Files/Folders
- [`linera-views/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-views/Cargo.toml).
- [`linera-views/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-views/src/lib.rs).
- [`linera-views/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-views/src): Modules like batch.rs, common.rs, context.rs, graph_ql.rs, hashing.rs, key_value_store_view.rs, log_view.rs, lru_caching.rs, map_view.rs, memory.rs, queue_view.rs, reentrant_collection_view.rs, register_view.rs, rocksdb.rs, scoped_view.rs, set_view.rs, test_utils.rs, views.rs.
- [`linera-views-derive/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-views-derive/src/lib.rs): Macros.

### Learning Path
1. Core views in linera-views.
2. Macros in derive crate.

### 2.4 linera-execution
Runtime for applications.

#### Key Files/Folders
- [`linera-execution/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-execution/Cargo.toml).
- [`linera-execution/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-execution/src/lib.rs).
- [`linera-execution/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-execution/src): Modules like applications.rs, committee.rs, error.rs, prices.rs, query.rs, resource_control.rs, system.rs, test_utils.rs, user.rs, wasm/.

### Learning Path
1. Execution logic in user and wasm modules.

### 2.5 linera-chain
Chain and messaging logic.

#### Key Files/Folders
- [`linera-chain/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-chain/Cargo.toml).
- [`linera-chain/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-chain/src/lib.rs).
- [`linera-chain/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-chain/src): Modules like chain.rs, data_types.rs, test.rs.

### Learning Path
- Focus on data_types and chain.

### 2.6 linera-storage
Storage abstractions.

#### Key Files/Folders
- [`linera-storage/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-storage/Cargo.toml).
- [`linera-storage/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-storage/src/lib.rs).
- [`linera-storage/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-storage/src): Modules like db_storage.rs, memory.rs, store.rs, test_utils.rs.

### Learning Path
- Storage interfaces.

**Tips**: Each crate has tests/ subfolder; run `cargo test` for learning.

**Transition**: Move to supporting crates for interfaces and tools.

## 3. Supporting Crates (Tools and Interfaces)
Crates for RPC, clients, services, and SDK.

### 3.1 linera-rpc
RPC messages.

#### Key Files/Folders
- [`linera-rpc/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-rpc/Cargo.toml).
- [`linera-rpc/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-rpc/src/lib.rs).
- [`linera-rpc/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-rpc/src): Modules like batch_pusher.rs, chain_filters.rs, client.rs, config.rs, cross_chain.rs, mass_client.rs, message.rs, node_provider.rs, simple_client.rs, transport.rs, unit_tests/.

### Learning Path
- Message and config modules.

### 3.2 linera-core
Core protocol logic.

#### Key Files/Folders
- [`linera-core/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-core/Cargo.toml).
- [`linera-core/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-core/src/lib.rs).
- [`linera-core/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-core/src): Modules like client.rs, local_node.rs, node.rs, notifier.rs, tracker.rs, unit_tests/, worker.rs.

### Learning Path
- Node and worker.

### 3.3 linera-client
Client libraries.

#### Key Files/Folders
- [`linera-client/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-client/Cargo.toml).
- [`linera-client/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-client/src/lib.rs).
- [`linera-client/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-client/src): Modules like chain_listener.rs, client_context.rs, client_options.rs, config.rs, persister.rs, wallet.rs.

### Learning Path
- Wallet and config.

### 3.4 linera-service
Executables for nodes.

#### Key Files/Folders
- [`linera-service/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-service/Cargo.toml).
- [`linera-service/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-service/src/lib.rs).
- [`linera-service/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-service/src): Modules like chain_worker.rs, cli_wrappers.rs, faucet.rs, grpc_network.rs, project.rs, project_test.rs, storage.rs, util.rs, validator_node.rs, walle t.rs.

### Learning Path
- Chain worker and validator.

### 3.5 linera-sdk and linera-sdk-derive
App development tools.

#### Key Files/Folders
- [`linera-sdk/Cargo.toml`](https://github.com/linera-io/linera-protocol/blob/main/linera-sdk/Cargo.toml).
- [`linera-sdk/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-sdk/src/lib.rs).
- [`linera-sdk/src/`](https://github.com/linera-io/linera-protocol/tree/main/linera-sdk/src): Modules like abi.rs, contract.rs, graphql.rs, service.rs, test.rs, util.rs, views.rs, wasm/.
- [`linera-sdk-derive/src/lib.rs`](https://github.com/linera-io/linera-protocol/blob/main/linera-sdk-derive/src/lib.rs): Macros.

### Learning Path
1. SDK for app writing.
2. Derive for macros.

**Tips**: Build apps using SDK.

**Transition**: Apply with examples.

## 4. Examples (Hands-On Applications)
Practical Rust apps to test protocol.

### Key Folders/Files
- [`examples/`](https://github.com/linera-io/linera-protocol/tree/main/examples): Subfolders like aml, counter, crowd_funding, fungible, matching_engine, meta, non_fungible_token, ownable, social.

### Learning Path
1. Start with simple like counter.
2. Advance to fungible, social.

**Tips**: Deploy via [`README COUNTER QUICK START`](https://github.com/linera-io/linera-protocol/tree/main/examples/counter)

**Transition**: Explore benches and scripts for performance.

## 5. Advanced Tools (Scripts)
Performance tests and utilities.

### Key Folders/Files
- [`scripts/`](https://github.com/linera-io/linera-protocol/tree/main/scripts): Helper scripts like run_local.sh.


## 6. High-Level Overview (Protocol Fundamentals)
Conceptual introduction to Linera.

### Key Files
- [`src/protocol/overview.md`](https://github.com/linera-io/linera-documentation/blob/main/src/protocol/overview.md)
- [`src/protocol/use_cases.md`](https://github.com/linera-io/linera-documentation/blob/main/src/protocol/use_cases.md)
- [`src/protocol/roadmap.md`](https://github.com/linera-io/linera-documentation/blob/main/src/protocol/roadmap.md)

### Learning Path
1. Overview.
2. Use cases.
3. Roadmap.

## 7. Developers Guide (Building Applications)
Setup, concepts, backends, frontends, experimental, advanced.

### 7.1 Getting Started
- [`src/developers/getting_started.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/getting_started.md)
- [`src/developers/getting_started/installation.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/getting_started/installation.md)
- [`src/developers/getting_started/hello_linera.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/getting_started/hello_linera.md)

### 7.2 Core Concepts
- [`src/developers/core_concepts.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/core_concepts.md)

### 7.3 Writing Backends
- [`src/developers/backend.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/backend.md)
- And subfiles like abi.md, contract.md, etc.

### 7.4 Writing Frontends
- [`src/developers/frontend.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/frontend.md)
- Subfiles: overview.md, setup.md, interactivity.md.

### 7.5 Experimental Features
- [`src/developers/experimental.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/experimental.md)
- Subfiles: ml.md, ethereum.md.

### 7.6 Advanced Topics
- [`src/developers/advanced_topics.md`](https://github.com/linera-io/linera-documentation/blob/main/src/developers/advanced_topics.md)
- Subfiles: block_creation.md, validators.md, etc.

## 8. Operators Guide (Running Infrastructure)
Devnets and testnets.

### 8.1 Devnets
- [`src/operators/devnets.md`](https://github.com/linera-io/linera-documentation/blob/main/src/operators/devnets.md)
- Subfiles: kind.md, compose.md.

### 8.2 Testnets
- [`src/operators/testnets.md`](https://github.com/linera-io/linera-documentation/blob/main/src/operators/testnets.md)
- Subfiles: manual-installation.md.

## 9. Appendix (Additional Resources)
- [`src/appendix/glossary.md`](https://github.com/linera-io/linera-documentation/blob/main/src/appendix/glossary.md)
- [`src/appendix/videos.md`](https://github.com/linera-io/linera-documentation/blob/main/src/appendix/videos.md)

## Additional Repo Navigation Tips
- **Root Files**: [`LICENSE`](https://github.com/linera-io/linera-protocol/blob/main/LICENSE), [`book.toml`](https://github.com/linera-io/linera-documentation/blob/main/book.toml) for mdBook in docs repo.
- **Building**: Use Cargo for code; mdBook for docs.
- **Search**: GitHub search for keywords.
  
This guide sequences content to build knowledge progressively: concepts → building → operating → references. Revisit sections as needed for reinforcement. For updates, check the repo commits.
