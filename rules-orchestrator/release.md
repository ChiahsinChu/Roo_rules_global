# Release Preparation Protocol

## Context

**Trigger:** Pre-release Check / Version Bump
**Goal:** Ensure documentation consistency across `CHANGELOG.md` and `CITATION.cff` prior to tagging.

---

## Rule 1: CHANGELOG Consistency

**Objective:** The Changelog must reflect the delta between the current state and the previous stable release.

### Instructions:

1.  **Identify Previous Tag:** Retrieve the latest Git tag (e.g., `git describe --tags --abbrev=0`).
2.  **Generate Diff:** Compare the current `HEAD` against the previous tag to list all merged pull requests and commits.
    - _Command:_ `git log <PREVIOUS_TAG>..HEAD --oneline`
3.  **Verify Content:**
    - Ensure all significant user-facing changes (features, fixes) from the git log are represented in the latest section of `CHANGELOG.md`. Use `[Unreleased]` as the latest section, unless a new version (to be released) is specified. 
    - Group changes by category: `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`.

**Success Criteria:**

- [ ] `CHANGELOG.md` contains a new entry for the target version.
- [ ] No significant commits from the git log are missing from the entry.

---

## Rule 2: CITATION.cff Synchronization

**Objective:** Citation metadata must match the new version artifact exactly.

### Instructions:

1.  **Update `version`:**
    - Set the `version:` key to the exact semantic version number intended for this release (e.g., `1.2.0`).
2.  **Update `date-released`:**
    - Set the `date-released:` key to the current date in `YYYY-MM-DD` format.
3.  **Update `identifiers`:**
    - Locate the `identifiers` list.
    - If a specific DOI or URL is version-dependent (e.g., a Zenodo reservation), update the `value:` field to match the new reservation.
    - _Note:_ If the DOI is immutable (represents all versions), leave as is. If it represents the specific release, ensure the reserved DOI is present.

**Success Criteria:**

- [ ] `version` matches the target release.
- [ ] `date-released` is today's date.
- [ ] `identifiers/value` is accurate for the new release.
