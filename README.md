# Install rust-toolchain.toml

This GitHub action installs the Rust toolchain specified in the specified [toolchain file (`rust-toolchain.toml)`](https://rust-lang.github.io/rustup/overrides.html#the-toolchain-file) using [`dtolnay/rust-toolchain`](https://github.com/dtolnay/rust-toolchain) and [yq](https://github.com/mikefarah/yq).

## Usage

```yaml
- uses: mkroening/rust-toolchain-toml@main
  with:
    # Path to the toolchain file.
    # Default: rust-toolchain.toml
    toolchain-file: ''
```

## Example workflow

```yaml
name: test suite
on: [push, pull_request]

jobs:
  test:
    name: cargo test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: mkroening/rust-toolchain-toml@main
      - run: cargo test --all-features
```

## License

The scripts and documentation in this project are released under the [MIT
License](LICENSE).
