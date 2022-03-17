# 🐍🐍 molting Release Action

GitHub Action to automate releases using [`molting`](https://github.com/lucasmelin/molting).

## Examples

### Trigger a new version on every push
```yaml
on: [push]

jobs:
  molting_job:
    runs-on: ubuntu-latest
    name: Update the project version
    steps:
      - uses: actions/checkout@v2
      - uses: lucasmelin/molting-release-action@v1
```

### Manually trigger a release
```yaml
on:
  workflow_dispatch:
    inputs:
      version:
        type: choice
        description: Choose the type of release
        options:
          - patch
          - minor
          - major

jobs:
  molting_job:
    runs-on: ubuntu-latest
    name: Update the project version
    steps:
      - uses: actions/checkout@v2
      - uses: lucasmelin/molting-release-action@v1
        with:
          version: ${{ github.event.inputs.version }}
```
