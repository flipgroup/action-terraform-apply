# Action Terraform apply

GitHub Action that will configure a workflow for executing [`terraform apply`](https://developer.hashicorp.com/terraform/cli/commands/apply) operations in CI/CD pipelines for a given workspace.

## Usage

```yaml
jobs:
  main:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout source
        uses: actions/checkout@v4
      - name: Setup Terraform
        uses: flipgroup/action-terraform-apply@main
        with:
          version: 1.7.5
          workspace: prod

      # workflow now configured for use with terraform

      - name: Terraform apply
        run: |
          cd ops/my-terraform-configuration
          terraform init
          terraform apply
```

Optionally, the Action can configure the following properties, allowing use of a private GitHub repository as a [Module source](https://developer.hashicorp.com/terraform/language/modules/sources#github) for Terraform configurations:

- Start `ssh-agent` and add a given SSH private key.
- Configure `git` with a HTTPS -> SSH clone target [`url.<base>.insteadOf`](https://git-scm.com/docs/git-config#Documentation/git-config.txt-urlltbasegtinsteadOf) rewrite.

```yaml
jobs:
  main:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout source
        uses: actions/checkout@v4
      - name: Setup Terraform
        uses: flipgroup/action-terraform-apply@main
        with:
          version: 1.7.5
          workspace: prod
          ssh-private-key: ${{ secrets.SSH_PRIVATE_KEY }}
          github-module-repository: owner/module-repository
```
