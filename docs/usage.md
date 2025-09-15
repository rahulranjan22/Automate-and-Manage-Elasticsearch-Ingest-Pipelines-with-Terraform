## Usage

This guide walks you through setting up and operating Terraform-managed Elasticsearch ingest pipelines.

### Prerequisites
- Terraform >= 1.5
- Access to an Elasticsearch cluster and credentials with pipeline management permissions
- Optional: Make, Docker, or CI runner

### Repository Layout (proposed)
```
terraform/
  modules/
    ingest_pipeline/
  envs/
    dev/
    prod/
docs/
```

### Setup
1. Initialize Terraform in your chosen environment directory:
   ```bash
   terraform -chdir=terraform/envs/dev init
   ```
2. Review variables in `terraform/envs/dev/terraform.tfvars` and set values as needed.
3. Create or update pipeline definitions (JSON) referenced by the module.

### Plan Changes
```bash
terraform -chdir=terraform/envs/dev plan -out=plan.tfplan
```

### Apply Changes
```bash
terraform -chdir=terraform/envs/dev apply -auto-approve plan.tfplan
```

### Workspaces for Multiple Environments
```bash
terraform -chdir=terraform/envs dev workspace new staging || true
terraform -chdir=terraform/envs dev workspace select staging
```

### CI/CD Example (GitHub Actions sketch)
```yaml
name: Terraform
on: [push]
jobs:
  plan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: hashicorp/setup-terraform@v3
      - run: terraform -chdir=terraform/envs/dev init -input=false
      - run: terraform -chdir=terraform/envs/dev plan -input=false -lock=false
  apply:
    if: github.ref == 'refs/heads/main'
    needs: plan
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: hashicorp/setup-terraform@v3
      - run: terraform -chdir=terraform/envs/dev init -input=false
      - run: terraform -chdir=terraform/envs/dev apply -input=false -auto-approve
```

### Rollback Strategy
- Keep previous pipeline definitions in version control.
- Use `terraform state show` to inspect current resources.
- Re-apply a known-good commit to revert.

