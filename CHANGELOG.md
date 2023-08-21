# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
## [Unreleased]

### Forge

#### Added

- support for `keccak_syscall` syscall. It can be used directly in cairo tests

### Cast

#### Added

- `accounts-file` field in Scarb.toml profile

## [0.4.0] - 2023-08-17

### Forge

#### Added

- `#[should_panic]` attribute support
- Documentation to public methods
- Information sections to documentation about importing `snforge_std`
- Print support for basic numeric data types
- Functions `parse_txt` and `TxtParser<T>::deserialize_txt` to load data from plain text files and serialize it
- `get_class_hash` cheatcode
- `mock_call` cheatcode
- `precalculate_address` cheatcode


#### Changed

- Exported `snforge_std` as a Scarb package, now you have to import it explicitly with e.g. `use snforge_std::declare`
  and add it as a dependency to your Scarb.toml

```toml
[dependencies]
# ...
snforge_std = { git = "https://github.com/foundry-rs/starknet-foundry", tag = "0.4.0" }
```

- Moved `ForgeConfigFromScarb` to `scarb.rs` and renamed to `ForgeConfig`
- Made private:
    - `print_collected_tests_count`
    - `print_running_tests`
    - `print_test_result`
    - `print_test_summary`
    - `TestCaseSummary::from_run_result`
    - `TestCaseSummary::skipped`
    - `extract_result_data`
    - `StarknetArtifacts`
    - `StarknetContractArtifactPaths`
    - `StarknetContract`
- Split `dependencies_for_package` into separate methods:
    - `paths_for_package`
    - `corelib_for_package`
    - `target_name_for_package`
    - `compilation_unit_for_package`

- Fails test when user tries to use syscalls not supported by forge test runner
- Updated cairo-lang to 2.1.0, starknet-api to 0.4.1 and blockifier to 0.2.0-rc0

### Cast

#### Added

- Added `--class-hash` flag to account create/deploy, allowing for custom openzeppelin account contract class hash 

## [0.3.0] - 2023-08-02

### Forge

#### Added

- `warp` cheatcode
- `roll` cheatcode
- `prank` cheatcode
- Most unsafe libfuncs can now be used in contracts

#### Changed

- `declare` return type to `starknet::ClassHash`, doesn't return a `Result`
- `PreparedContract` `class_hash` changed to `starknet::ClassHash`
- `deploy` return type to `starknet::ContractAddress`

#### Fixed

- Using the same cairo file names as corelib files no longer fails test execution

### Cast

#### Added

- multicall as a single transaction
- account creation and deployment
- `--wait` flag to wait for transaction to be accepted/rejected

#### Changed

- sierra and casm artifacts are now required in Scarb.toml for contract declaration
- improved error messages

## [0.1.1] - 2023-07-26

### Forge & Cast

#### Fixed

- `class_hash`es calculation
- Test collection

## [0.1.0] - 2023-07-19

### Forge & Cast

#### Added

- Initial release