## Examples

End-to-end examples for managing Elasticsearch ingest pipelines with Terraform.

### Example 1: Simple Grok Pipeline
Files:
- `terraform/envs/dev` with pipeline variables
- `pipelines/simple_grok.json` referenced by the module

Usage:
```bash
terraform -chdir=terraform/envs/dev init
terraform -chdir=terraform/envs/dev apply -auto-approve
```

### Example 2: Enrich Processor with Lookup Index
Demonstrates managing dependencies between ingest pipeline and index templates.

### Example 3: Multi-Environment Promotion
Illustrates using workspaces or separate env directories for dev/staging/prod.

