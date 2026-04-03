# .github

Shared CI/CD workflows and composite actions for the [dkdc-io](https://github.com/dkdc-io) organization.

## Reusable workflows

| Workflow | Description | Key inputs |
|----------|-------------|------------|
| `check.yml` | CI checks (Rust + optional Python) | `python` (bool), `python-version` |
| `release-python.yml` | Build + publish wheels to PyPI via OIDC | `python-version` |

## Composite actions

| Action | Description | Key inputs |
|--------|-------------|------------|
| `publish-crate` | Idempotent crates.io publish with index wait | `crate`, `sleep`, `last` |

## Usage

```yaml
# ci.yml — call the shared check workflow
jobs:
  check:
    uses: dkdc-io/.github/.github/workflows/check.yml@v1
```

```yaml
# release-rust.yml — use the publish-crate action
steps:
  - uses: dkdc-io/.github/actions/publish-crate@v1
    with:
      crate: my-crate
      last: "true"
```
