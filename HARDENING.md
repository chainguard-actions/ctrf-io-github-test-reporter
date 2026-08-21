<!-- markdownlint-disable -->

# Hardening Report: ctrf-io--github-test-reporter/v1.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ctrf-io--github-test-reporter/v1.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference GitHub Actions using mutable version tags (e.g. @v6, @v1) instead of immutable 40-character commit SHA pins. This exposes the workflow to supply-chain attacks: if the referenced action's tag is moved to a different (potentially malicious) commit, the workflow will silently execute the new code. Affected references include: actions/checkout@v6, actions/setup-node@v6, and ctrf-io/github-test-reporter@v1. All should be pinned to full SHA digests, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/main.yaml:25`
- `.github/workflows/main.yaml:28`
- `.github/workflows/main.yaml:52`
- `.github/workflows/main.yaml:55`
- `.github/workflows/main.yaml:65`
- `.github/workflows/main.yaml:84`
- `.github/workflows/main.yaml:87`
- `.github/workflows/main.yaml:103`
- `.github/workflows/main.yaml:106`
- `.github/workflows/action-self-test.yaml:26`
- `.github/workflows/action-self-test.yaml:28`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all unpinned action references in both workflow files:
- .github/workflows/main.yaml: Replaced all 8 occurrences of actions/checkout@v6, actions/setup-node@v6, and ctrf-io/github-test-reporter@v1 with full SHA pins.
- .github/workflows/action-self-test.yaml: Replaced all 24 occurrences of actions/checkout@v6 and actions/setup-node@v6 with full SHA pins.

SHAs resolved:
- actions/checkout@v6 → d23441a48e516b6c34aea4fa41551a30e30af803
- actions/setup-node@v6 → 249970729cb0ef3589644e2896645e5dc5ba9c38
- ctrf-io/github-test-reporter@v1 → 7974087018bf4857cf5a9d78723e152038c3fa31

All references use the format 'owner/repo@<full-sha> # tag' to preserve readability.

