# Action Terraform apply

GitHub Action for setting up a workflow to execute [`terraform apply`](https://developer.hashicorp.com/terraform/cli/commands/apply) operations in CI/CD pipelines for a given workspace.

## Usage

```yaml
jobs:
  main:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout source
        uses: actions/checkout@v3
      - name: Setup Terraform
        uses: flipgroup/action-terraform-apply@main
        with:
          version: 1.3.6
          workspace: prod

      # -- as an example --

      - name: Terraform apply
        run: |
          cd ops/my-terraform-configuration
          terraform init
          terraform apply
```
