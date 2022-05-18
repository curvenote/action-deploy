# Curvenote GitHub Action: Deploy

## Description

This GitHub action allows you to automate deploying a website to the `curve.space` hosting service. In order to deploy a website, the repository must have a `curvenote.yml` file at the repository root.

Configure your repository using the curvenote command line tool (cli) - see [docs.curvenote.com](https://docs.curvenote.com/cli) on how to install the cli. Once installed the `curvenote init` command will collect information and create your `curvenote.yml` file, commit this to the repository and push.

Note: also consider adding the `_build/` to your `.gitignore` file, if you are testing your website locally.

## Basic Usage

To deploy using github actions, add a new file to your repository at `.github/workflows/deploy.yml` containing:

```yaml
name: Curvenote Deploy
on:
  push:
    branches:
      - main
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to curve.space
        uses: curvenote/action-deploy@v1
        env:
          CURVENOTE_TOKEN: ${{ secrets.CURVENOTE_TOKEN }}
```

This requires your Curvenote API token to be saved in your GitHub secrets under `CURVENOTE_TOKEN`. See [Authorization](https://docs.curvenote.com/cli/authorization) for how to generate an API token. To add a secret see the [GitHub docs](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository).

### Options

You can add options for the deployment using the `with` field in the action step.

```yaml
steps:
  - uses: actions/curvenote-deploy@v1
    with:
      pull: true
```

- `pull` (optional) when set to `true` the action will attempt to pull the latest versions of any linked projects from curvenote.com.

## Support

Open an isue on this repo and we'll respond. 🚀
