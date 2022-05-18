# Curvenote GitHub Action: Deploy

## Description

This GitHub action allows you to automate deploying a website to the `curve.space` hosting service. In order to deploy a website, the repository must have a `curvenote.yml` file at the repository root.

Configure your repository using the curvenote command line tool (cli) - see [docs.curvenote.com](https://docs.curvenote.com/cli) on how to install the cli. Once installed the `curvenote init` command will collect information and create your `curvenote.yml` file, commit this to the repository and push.

Note: also consider adding the `_build/` to your `.gitignore` file, if you are testing your website locally.

## Basic Usage

To deploy using github actions, add a new file to your repository at `.github/workflows/main.yml` containing:

```yaml
name: Curvenote Deploy
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Deploy
      uses: actions/curvenote-deploy@v1
      with:
        pull: true
      env:
        CURVENOTE_TOKEN: ${{ secrets.CURVENOTE_TOKEN }}
```

This requires your Curvenote API token to be saved in your GitHub secrets under `CURVENOTE_TOKEN`. See [Authorization](https://docs.curvenote.com/cli/authorization) for how to generate an API token.

### Options

- `pull` (optional) when set to `true` the action will attempt to pull that latest versions of any linked projects from curvenote.com

## Support

Open an isue on this repo and we'll respond. 🚀
