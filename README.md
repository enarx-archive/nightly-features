# allowed-nightly-features

A Github Action that tests which nightly features your Rust code enables, and
checks those enabled features against an allowlist you provide.

If unallowed features are enabled, the test will point out the offending files
and features.

## Usage

Include the action as part of a workflow that performs a checkout, and provide
a comma-separated list of the features you'd like to allow as input to the
action under the `allowed_features` name.

The following example will allow only the `asm`, `raw_ref_macros`, and
`ptr_offset_from` features to be enabled:

```yml
name: check-nightly-features

on:
  pull_request

jobs:
  check-nightly-features:
    runs-on: ubuntu-latest
    steps:
    - name: checkout
      uses: actions/checkout@v2
    - uses: enarx/nightly-features@master
      with:
        allowed_features: 'asm, raw_ref_macros, ptr_offset_from'
```
