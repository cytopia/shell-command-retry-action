# Shell command retry action


[![GitHub release](https://img.shields.io/github/release/cytopia/shell-command-retry-action.svg?logo=github)](https://github.com/cytopia/shell-command-retry-action/releases/latest)
[![GitHub marketplace](https://img.shields.io/badge/marketplace-shell--command--retry--action-blue?logo=github)](https://github.com/marketplace/actions/shell-command-retry-action)
[![](https://img.shields.io/badge/github-cytopia%2Fshell--command--retry--action-red.svg?logo=github)](https://github.com/cytopia/shell-command-retry-action "github.com/cytopia/shell-command-retry-action")
[![test](https://github.com/cytopia/shell-command-retry-action/actions/workflows/test.yml/badge.svg)](https://github.com/cytopia/shell-command-retry-action/actions/workflows/test.yml)


## Usage

```yaml
on: [push]

jobs:
  job1:
    runs-on: ubuntu-latest
    name: Pull docker image
    steps:

      - name: Checkout repository
        uses: actions/checkout@v2
        with:
          fetch-depth: 0

      - name: Build docker image
        uses: cytopia/shell-command-retry-action@v0.1
          with:
            retries: 10
            pause: 10
            command: |
              docker build -t test .
```
