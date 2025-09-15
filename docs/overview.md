## Overview

This project provides a structured approach to automate, version, and operate Elasticsearch ingest pipelines using Terraform. It is intended for platform teams who need reproducible, auditable, and environment-aware pipeline management.

Key capabilities:
- Declarative pipeline definitions managed in version control
- Environment-aware configuration via variables and workspaces
- CI/CD-friendly workflows for plan and apply
- Drift detection and safe rollouts
- Examples and templates to accelerate adoption

High-level architecture:
1. Author pipeline JSON definitions and Terraform modules.
2. Validate and plan changes in CI using non-interactive commands.
3. Apply approved changes to the target Elasticsearch cluster(s).
4. Monitor and iterate using versioned changes.

