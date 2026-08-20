<!-- markdownlint-disable -->

# Hardening Report: softprops--turnstyle/v3.2.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **softprops--turnstyle/v3.2.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### missing-permissions (severity: medium)

The workflow file .github/workflows/main.yml has no top-level `permissions:` key, and neither the `build` job nor the `integration` job defines its own `permissions:` block. This means the workflow runs with GitHub's default permissions, which may be broader than necessary. A minimal permissions block (e.g., `contents: read`) should be added at the top level or per job.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** missing-permissions

**Notes:**

Added a top-level `permissions:` block to `.github/workflows/main.yml` with `contents: read` (required for checkout steps in both jobs) and `actions: read` (required for the Turnstyle action in the integration job, which monitors GitHub Actions workflow runs). This replaces the implicit default permissions with the minimum necessary.

