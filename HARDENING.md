<!-- markdownlint-disable -->

# Hardening Report: ctrf-io--github-test-reporter/v1.0.24

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ctrf-io--github-test-reporter/v1.0.24** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All 17 `uses: actions/checkout@v4` references in the workflow use a mutable tag (`@v4`) instead of a full 40-character commit SHA. This means a compromised or altered tag could silently substitute malicious code. Each job's checkout step is affected. Example failing reference: `uses: actions/checkout@v4`. These should be pinned to a specific SHA, e.g. `uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/build-and-test.yaml:18`
- `.github/workflows/build-and-test.yaml:52`
- `.github/workflows/build-and-test.yaml:62`
- `.github/workflows/build-and-test.yaml:72`
- `.github/workflows/build-and-test.yaml:82`
- `.github/workflows/build-and-test.yaml:92`
- `.github/workflows/build-and-test.yaml:102`
- `.github/workflows/build-and-test.yaml:112`
- `.github/workflows/build-and-test.yaml:122`
- `.github/workflows/build-and-test.yaml:132`
- `.github/workflows/build-and-test.yaml:142`
- `.github/workflows/build-and-test.yaml:152`
- `.github/workflows/build-and-test.yaml:162`
- `.github/workflows/build-and-test.yaml:172`
- `.github/workflows/build-and-test.yaml:182`
- `.github/workflows/build-and-test.yaml:192`
- `.github/workflows/build-and-test.yaml:202`

### missing-permissions (severity: medium)

The workflow file `build-and-test.yaml` has no top-level `permissions:` key and none of its 14 jobs define a `permissions:` block. Without explicit permissions, the workflow inherits the repository's default token permissions (which may be `write-all` for older repositories or permissive org defaults). A minimal `permissions:` block should be added at the top level or per job to follow the principle of least privilege.

Locations:

- `.github/workflows/build-and-test.yaml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

1. Pinned all 17 `actions/checkout@v4` references to SHA `11d5960a326750d5838078e36cf38b85af677262 # v4` in `.github/workflows/build-and-test.yaml`. 2. Added top-level `permissions: contents: read` block to enforce least-privilege access — this is the minimum permission needed for checkout operations across all 14 jobs.

