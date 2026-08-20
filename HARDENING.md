<!-- markdownlint-disable -->

# Hardening Report: softprops--turnstyle/v3.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **softprops--turnstyle/v3.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### missing-permissions (severity: medium)

The workflow file .github/workflows/main.yml has no top-level `permissions:` key and neither of its jobs (`build`, `integration`) defines job-level permissions. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions, which violates the principle of least privilege. A top-level `permissions:` block with specific minimal scopes (e.g., `contents: read`) should be added.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** missing-permissions

**Notes:**

Added a top-level `permissions: contents: read` block to `.github/workflows/main.yml`. Both the `build` and `integration` jobs only require repository checkout access, so `contents: read` is the minimal sufficient permission. This replaces the implicit broad default GITHUB_TOKEN permissions with an explicit least-privilege grant.

