# circleci-trust-publish-test-unscoped

Unscoped test package for validating CircleCI OIDC trusted publishing against the **real npm registry**.

## Purpose

Used for bug-bashing the CircleCI trusted publisher UI flows on wubwub (unscoped package scenario). This package is connected to CircleCI and publishes via OIDC token exchange — no long-lived npm tokens.

## Setup

### 1. CircleCI

Connect this repo to CircleCI and run the `debug-workflow` to get claim values.

| Field | Value |
|-------|-------|
| Org ID | _TBD — run debug-workflow_ |
| Project ID | _TBD — run debug-workflow_ |
| Pipeline Definition ID | _TBD — run debug-workflow_ |

### 2. npm Trusted Publishing

Configure the trusted publisher on [npmjs.com](https://www.npmjs.com/package/circleci-trust-publish-test-unscoped/access) with the org-id and project-id from the debug workflow.

## Workflows

### `publish-workflow`
Publishes to the real npm registry. Only runs on `main`.

### `debug-workflow`
Decodes and prints OIDC token claims — use to get the values needed for trusted publisher configuration.

## Related

- [circleci-trust-publish-test](../circleci-trust-publish-test) — user-scoped version (`@owlstronaut`)
- [circleci-trust-publish-test-org](../circleci-trust-publish-test-org) — org-scoped version (`@owlstronaut-test-org`)
- Bug bash task: #14721
