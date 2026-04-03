# .github

Shared workflows and actions for the [dkdc-io](https://github.com/dkdc-io) organization.

## Reusable workflows

### check.yml

CI checks (Rust + optional Python). Called by each repo's `ci.yml`.

Inputs:
- `python` (boolean, default: true) — include Python setup and checks
- `python-version` (string, default: "3.14") — Python version

### release-python.yml

Build and publish Python wheels + sdist to PyPI via OIDC.

Inputs:
- `python-version` (string, default: "3.14") — Python version

## Composite actions

### publish-crate

Publish a single crate to crates.io with idempotency and index propagation delay.

Inputs:
- `crate` (required) — crate name
- `sleep` (default: "30") — seconds to wait after publish
- `last` (default: "false") — skip sleep for the last crate
