# Action Terraform apply

GitHub Action for setting up a workflow to execute [`terraform apply`](https://www.terraform.io/docs/cli/commands/apply.html) operations in CI/CD pipelines for a given workspace.

## Usage

```yaml
jobs:
  main:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout source
        uses: actions/checkout@v2
      - name: Setup Terraform
        uses: flipgroup/action-terraform-apply@main
        with:
          version: 1.1.5
          workspace: prod

      # -- as an example --

      - name: Terraform apply
        run: |
          cd ops/my-terraform-configuration
          terraform init
          terraform apply
```
