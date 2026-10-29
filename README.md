# Setup Passbolt Action

GitHub Action to install and configure [Passbolt CLI](https://github.com/passbolt/go-passbolt-cli) for use in workflows.

## Usage

```yaml
- uses: catalistapp/setup-passbolt-action@v1
  with:
    server-address: ${{ vars.PASSBOLT_URL }}
    password: ${{ secrets.PASSBOLT_PASS }}
    private-key: ${{ secrets.PASSBOLT_PRIVATE_KEY }}
```

## Inputs

| Input            | Description                  | Required | Default |
|------------------|------------------------------|----------|---------|
| `server-address` | Passbolt server URL          | Yes      | -       |
| `password`       | Passbolt user password       | Yes      | -       |
| `private-key`    | Passbolt private key         | Yes      | -       |
| `version`        | Passbolt CLI version         | No       | `0.4.1` |

## Example

```yaml
name: Deploy

on:
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: catalistapp/setup-passbolt-action@v1
        with:
          server-address: ${{ vars.PASSBOLT_URL }}
          password: ${{ secrets.PASSBOLT_PASS }}
          private-key: ${{ secrets.PASSBOLT_PRIVATE_KEY }}

      - name: Use passbolt
        run: passbolt exec -- echo "Secret injected"
```
