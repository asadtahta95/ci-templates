# CI Templates

Reusable GitHub Actions workflows for shell, Compose, and security scans. English-only. Used by `linux-docker-installer`, `linux-kubernetes-installer`, and `reverse-proxy-lab`.

## Quick Use (One snippet)

```yaml
# .github/workflows/lint.yml in your repo
name: lint
on: [push, pull_request]
jobs:
  call-shellcheck:
    uses: asadtahta95/ci-templates/.github/workflows/reusable-shellcheck.yml@main
  call-trivy:
    uses: asadtahta95/ci-templates/.github/workflows/reusable-trivy.yml@main
```

For Compose validation:

```yaml
jobs:
  call-compose:
    uses: asadtahta95/ci-templates/.github/workflows/reusable-compose.yml@main
    with:
      compose-file: traefik/docker-compose.yml
```

## What's inside

| Workflow | Purpose | Inputs |
|---|---|---|
| `reusable-shellcheck.yml` | shellcheck + `bash -n` for all `*.sh` | `severity` (default `warning`) |
| `reusable-compose.yml` | `docker compose config --quiet` validation | `compose-file` |
| `reusable-trivy.yml` | Trivy config/misconfig scan | `severity` (default `HIGH,CRITICAL`) |

See `examples/caller.yml` for a full copy-paste example.

## Pinning

For production, pin to a tag instead of `@main`:

```yaml
uses: asadtahta95/ci-templates/.github/workflows/reusable-shellcheck.yml@v1
```

## License

MIT
