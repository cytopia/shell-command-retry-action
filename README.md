# Shell command retry action

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
