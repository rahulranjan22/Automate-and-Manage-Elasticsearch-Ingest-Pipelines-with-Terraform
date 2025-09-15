## FAQ

### How do I update a pipeline safely?
Use a pull request with a Terraform plan. Apply only after review. Consider canary deployment by targeting a subset of indices first.

### Pipelines show drift. What should I do?
Inspect `terraform plan` output. If manual changes were made, re-apply the desired state from version control.

### Credentials management?
Use CI secrets or a vault. Avoid committing credentials. Prefer API keys with least privilege.

### How do I handle environment-specific settings?
Use variables and workspaces or separate `envs/` directories with their own `terraform.tfvars` files.

