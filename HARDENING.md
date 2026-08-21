<!-- markdownlint-disable -->

# Hardening Report: ctrf-io--github-test-reporter/v1.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ctrf-io--github-test-reporter/v1.2.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple `uses:` references in .github/workflows/main.yaml are pinned to mutable tags instead of immutable 40-character SHA digests, making the workflow vulnerable to supply-chain attacks if the referenced tags are moved. Failing references: `actions/checkout@v6` (line 24, 47, 72, 90), `actions/setup-node@v6` (line 27, 50, 75, 93), `ctrf-io/github-test-reporter@v1` (line 62).

Locations:

- `.github/workflows/main.yaml:24`
- `.github/workflows/main.yaml:27`
- `.github/workflows/main.yaml:47`
- `.github/workflows/main.yaml:50`
- `.github/workflows/main.yaml:62`
- `.github/workflows/main.yaml:72`
- `.github/workflows/main.yaml:75`
- `.github/workflows/main.yaml:90`
- `.github/workflows/main.yaml:93`

### unpinned-uses (severity: high)

Multiple `uses:` references in .github/workflows/action-self-test.yaml are pinned to mutable tags instead of immutable 40-character SHA digests, making the workflow vulnerable to supply-chain attacks if the referenced tags are moved. Failing references: `actions/checkout@v6` and `actions/setup-node@v6` appear in every job throughout the file (e.g., lines 25, 27 in the first job, and repeated across all subsequent jobs).

Locations:

- `.github/workflows/action-self-test.yaml:25`
- `.github/workflows/action-self-test.yaml:27`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable tag references to immutable SHA digests in both workflow files. In main.yaml: pinned actions/checkout@v6 (4x), actions/setup-node@v6 (4x), and ctrf-io/github-test-reporter@v1 (1x). In action-self-test.yaml: pinned actions/checkout@v6 (17x) and actions/setup-node@v6 (6x). All SHAs were resolved via lookup_action_sha and original tags are preserved as inline comments.

