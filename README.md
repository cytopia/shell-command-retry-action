# Shell command retry action

[![GitHub release](https://img.shields.io/github/release/cytopia/shell-command-retry-action.svg?logo=github)](https://github.com/cytopia/shell-command-retry-action/releases/latest)
[![GitHub marketplace](https://img.shields.io/badge/marketplace-shell--command--retry--action-blue?logo=github)](https://github.com/marketplace/actions/shell-command-retry-action)
[![](https://img.shields.io/badge/github-cytopia%2Fshell--command--retry--action-red.svg?logo=github)](https://github.com/cytopia/shell-command-retry-action "github.com/cytopia/shell-command-retry-action")
[![test](https://github.com/cytopia/shell-command-retry-action/actions/workflows/test.yml/badge.svg)](https://github.com/cytopia/shell-command-retry-action/actions/workflows/test.yml)

This action allows you to retry shell command for a few times in case they fail. This is especially useful for all kind of network related tasks, such as downloading files or similar. In case the remote endpoint has some issues, the job will not simply fail because of this, but retry the command and eventually reach success.


## :arrow_forward: Inputs

The following inputs can be used to alter the Docker tag name determination:

| Input     | Required | Default | Description                                |
|-----------|----------|----------|-------------------------------------------|
| `retries` | No       | `10`     | How many times to retry on failure.       |
| `pause`   | No       | `10`     | How many seconds to wait between retries. |
| `command` | Yes      | ``       | Shell command to execute                  |
| `workdir` | No       | ``       | Switch to this working directory prior executing the shell command |


## :arrow_backward: Outputs

None


## :computer: Usage

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
        uses: cytopia/shell-command-retry-action@v0.1.2
          with:
            retries: 10
            pause: 10
            command: |
              docker build -t test .
```


## :exclamation: Keep up-to-date with GitHub Dependabot

Since [Dependabot](https://docs.github.com/en/github/administering-a-repository/keeping-your-actions-up-to-date-with-github-dependabot) has [native GitHub Actions support](https://docs.github.com/en/github/administering-a-repository/configuration-options-for-dependency-updates#package-ecosystem), to enable it on your GitHub repo all you need to do is add the `.github/dependabot.yml` file:

```yml
version: 2
updates:
  # Maintain dependencies for GitHub Actions
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "daily"
```


## :octocat: [cytopia](https://github.com/cytopia) GitHub Actions

| Name                         | Description |
|------------------------------|-------------|
| [docker-tag-action]          | Determines Docker tags based on git branch, commit or git tag |
| [shell-command-retry-action] | Retries shell commands to avoid failing pipelines due to network issues |

[docker-tag-action]: https://github.com/cytopia/docker-tag-action
[shell-command-retry-action]: https://github.com/cytopia/shell-command-retry-action


## :page_facing_up: License

**[MIT License](LICENSE)**

Copyright (c) 2022 [cytopia](https://github.com/cytopia)
