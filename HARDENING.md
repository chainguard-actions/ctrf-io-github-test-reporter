<!-- markdownlint-disable -->

# Hardening Report: ctrf-io--github-test-reporter/v1.1.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ctrf-io--github-test-reporter/v1.1.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Workflow uses mutable tag references instead of pinned SHA hashes, making the workflow vulnerable to supply-chain attacks if the referenced action tags are moved or compromised. Failing references: `actions/checkout@v6`, `actions/setup-node@v6`, `ctrf-io/github-test-reporter@v1`. All should be pinned to full 40-character commit SHAs (e.g., `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`).

Locations:

- `.github/workflows/main.yaml:23`
- `.github/workflows/main.yaml:26`
- `.github/workflows/main.yaml:40`
- `.github/workflows/main.yaml:43`
- `.github/workflows/main.yaml:57`
- `.github/workflows/main.yaml:70`
- `.github/workflows/main.yaml:73`
- `.github/workflows/main.yaml:88`
- `.github/workflows/main.yaml:91`

### unpinned-uses (severity: high)

Workflow uses mutable tag references instead of pinned SHA hashes, making the workflow vulnerable to supply-chain attacks if the referenced action tags are moved or compromised. Failing references: `actions/checkout@v6`, `actions/setup-node@v6` (used across all jobs). All should be pinned to full 40-character commit SHAs.

Locations:

- `.github/workflows/action-self-test.yaml:22`
- `.github/workflows/action-self-test.yaml:24`
- `.github/workflows/action-self-test.yaml:55`
- `.github/workflows/action-self-test.yaml:68`
- `.github/workflows/action-self-test.yaml:80`
- `.github/workflows/action-self-test.yaml:93`
- `.github/workflows/action-self-test.yaml:106`
- `.github/workflows/action-self-test.yaml:119`
- `.github/workflows/action-self-test.yaml:131`
- `.github/workflows/action-self-test.yaml:143`
- `.github/workflows/action-self-test.yaml:155`
- `.github/workflows/action-self-test.yaml:167`
- `.github/workflows/action-self-test.yaml:179`
- `.github/workflows/action-self-test.yaml:192`
- `.github/workflows/action-self-test.yaml:194`
- `.github/workflows/action-self-test.yaml:214`
- `.github/workflows/action-self-test.yaml:216`
- `.github/workflows/action-self-test.yaml:236`
- `.github/workflows/action-self-test.yaml:238`
- `.github/workflows/action-self-test.yaml:258`
- `.github/workflows/action-self-test.yaml:260`
- `.github/workflows/action-self-test.yaml:284`
- `.github/workflows/action-self-test.yaml:286`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable action tag references to full 40-character commit SHAs in both workflow files:
- actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 # v6 (17 occurrences in action-self-test.yaml, 4 in main.yaml)
- actions/setup-node@v6 → @249970729cb0ef3589644e2896645e5dc5ba9c38 # v6 (6 occurrences in action-self-test.yaml, 4 in main.yaml)
- ctrf-io/github-test-reporter@v1 → @9ad85b91f851ff39e7da5f82981d30b9e637e163 # v1 (1 occurrence in main.yaml)
All SHAs were resolved via lookup_action_sha. Original tags preserved as inline comments for readability.

