## CLI and Make Targets

If you provide helper scripts or Make targets, document them here.

### Conventions
- All commands should be non-interactive and safe for CI/CD.
- Provide `--help` output examples where applicable.

### Examples
```bash
make init ENV=dev
make plan ENV=dev
make apply ENV=dev AUTO_APPROVE=true
```

