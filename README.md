# gda-test-pkg

This GitHub action tests the GAP package located in the current directory. Based on [gap-actions/run-pkg-tests](https://github.com/gap-actions/run-pkg-tests).


## Usage

This action can optionally be called in the workflow of a GAP package to run its tests.

### Inputs

  - `COVERAGE`:
    * Set to true to gather coverage
    * default: `false`
    * required: `false`
  - `GAP_TESTFILE`:
    * Name of the GAP file to be read for executing the package tests (overrides TestFile in PackageInfo.g)
    * default: `""`
    * required: `false`
  - `GAP_FLAGS`:
    * Additional flags to pass to the GAP executable
    * default: `false`
    * required: `false`
  - `ONLY_NEEDEDE`:
    * Only load necessary packages, not suggested ones, prior to testing
    * default: `false`
    * required: `false`
  - `ALL_PACKAGES`:
    * Load all packages prior to testing
    * default: `false`
    * required: `false`

### Example

```yaml
name: CI

on:
  - push
  - pull_request
  - workflow_dispatch

jobs:
  test:
    name: "Test the GAP package"
    runs-on: ubuntu-latest

    container:
      image: ghcr.io/stertooy/gda-image:master-slim

    steps:
      - uses: actions/checkout@v3
      - uses: stertooy/gda-build-pkg@v1
      - uses: stertooy/gda-test-pkg@v1
```
