# Setup Regal

> [!WARNING]
> This action is WIP and doesn't work... yet

GitHub action to configure the [Regal](https://github.com/StyraInc/regal) CLI.

## Basic Usage

The following example shows how to use the action to install the latest version of Regal and lint some files
in `policy`:

```yml
name: Run Regal Lint Check
on: [push]
jobs:
  lint-rego:
    runs-on: ubuntu-latest
    steps:
    - name: Check out repository code
      uses: actions/checkout@v3

    - name: Setup Regal
      uses: StyraInc/setup-regal@v1
      with:
        version: latest

    - name: Lint
      run: regal lint policy
```

## Choose Regal Version

### Using Latest

Using the latest version of Regal allows you to keep up-to-date with the latest Rules and best practices. However,
it might mean that policies that once passed, will need to be updated to pass with the latest version of Regal's rules.

> [!NOTE]  
> You can always disable rules using [Regal config](https://docs.styra.com/regal/#configuration).

```yml
steps:
  - name: Setup Regal
    uses: StyraInc/setup-regal@v1
    with:
      version: latest
```

It's also possible to use a pinned version of Regal. This is recommended for pipelines that deploy to production
environments.

```yml
steps:
  - name: Setup Regal
    uses: StyraInc/setup-regal@v1
    with:
      version: x.y.z
```

You can also use a SemVer or [SemVer range](https://www.npmjs.com/package/semver#ranges).

```yml
steps:
  - name: Setup Regal
    uses: StyraInc/setup-regal@v1
    with:
      version: 0.44
```

```yml
steps:
  - name: Setup Regal
    uses: StyraInc/setup-regal@v1
    with:
      version: <0.44
```

## Inputs

The action supports the following inputs:

- `version`: Optional, defaults to `latest`. [SemVer ranges](https://www.npmjs.com/package/semver#ranges) are supported too.
- `github-token`: Optional, defaults to `${{ github.token }}`. 

## Credits

This repo is based on the [Setup OPA Action](https://github.com/open-policy-agent/setup-opa).

## Community

For questions, discussions and announcements related to Styra products, services and open source projects, please join
the Styra community on [Slack](https://communityinviter.com/apps/styracommunity/signup)!