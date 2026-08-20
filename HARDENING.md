<!-- markdownlint-disable -->

# Hardening Report: softprops--turnstyle/v3.2.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **softprops--turnstyle/v3.2.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### missing-permissions (severity: medium)

The workflow file .github/workflows/main.yml has no top-level `permissions:` key, and neither the `build` job nor the `integration` job defines its own `permissions:` block. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (write access to contents, etc.). A minimal permissions block (e.g. `permissions: read-all` or specific scopes) should be added at the top level or per job.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** missing-permissions

**Notes:**

Added a top-level `permissions:` block to `.github/workflows/main.yml` with `contents: read` (for actions/checkout) and `actions: read` (for the turnstyle action to query workflow run status). This replaces the implicit default token permissions with explicit minimal scopes.

