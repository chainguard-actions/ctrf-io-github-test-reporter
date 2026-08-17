<!-- markdownlint-disable -->

# Hardening Report: ctrf-io--github-test-reporter/v1.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ctrf-io--github-test-reporter/v1.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple `uses:` references in this workflow use mutable version tags instead of pinned full-length SHA commit hashes. This exposes the workflow to supply-chain attacks if the referenced action tag is moved or compromised. Failing references include: `actions/checkout@v6`, `actions/setup-node@v6`, and `ctrf-io/github-test-reporter@v1`. All should be replaced with their corresponding 40-character commit SHAs (e.g. `actions/checkout@<40-char-sha> # v6`).

Locations:

- `.github/workflows/main.yaml:22`
- `.github/workflows/main.yaml:25`
- `.github/workflows/main.yaml:55`
- `.github/workflows/main.yaml:68`
- `.github/workflows/main.yaml:71`
- `.github/workflows/main.yaml:88`
- `.github/workflows/main.yaml:91`
- `.github/workflows/action-self-test.yaml:25`
- `.github/workflows/action-self-test.yaml:27`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all unpinned action references in both .github/workflows/main.yaml and .github/workflows/action-self-test.yaml:
- actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 # v6 (4 occurrences in main.yaml, 17 in action-self-test.yaml)
- actions/setup-node@v6 → @249970729cb0ef3589644e2896645e5dc5ba9c38 # v6 (4 occurrences in main.yaml, 6 in action-self-test.yaml)
- ctrf-io/github-test-reporter@v1 → @e500b992f936420eb633c91644cf10d4d71df700 # v1 (1 occurrence in main.yaml)
All SHAs were resolved using lookup_action_sha. No unpinned references remain.

