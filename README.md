# Install rust-toolchain.toml

This GitHub action installs the Rust toolchain specified in the specified [toolchain file (`rust-toolchain.toml`)](https://rust-lang.github.io/rustup/overrides.html#the-toolchain-file) using [`dtolnay/rust-toolchain`](https://github.com/dtolnay/rust-toolchain) and [yq](https://github.com/mikefarah/yq).

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

## Inputs

All inputs are optional.

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>toolchain-file</code></td>
  <td>
    Path to a <code>rust-toolchain.toml</code>.
  </td>
  <td><code>toolchain</code></td>
  <td>
    Rustup toolchain specifier e.g. <code>stable</code>, <code>nightly</code>, <code>1.42.0</code>, <code>nightly-2022-01-01</code>.
  </td>
</tr>
</table>

## Outputs

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>cachekey</code></td>
  <td>A short hash of the installed rustc version, appropriate for use as a cache key. <code>"20220627a831"</code></td>
</tr>
<tr>
  <td><code>name</code></td>
  <td>Rustup's name for the selected version of the toolchain, like <code>"1.62.0"</code>. Suitable for use with <code>cargo +${{steps.toolchain.outputs.name}}</code>.</td>
</tr>
</table>

## License

The scripts and documentation in this project are released under the [MIT
License](LICENSE).
