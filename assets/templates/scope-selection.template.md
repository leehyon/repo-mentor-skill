# Scope Selection

## Purpose

This document helps choose or refine a manageable module scope for `repo-mentor`.

It is **not** a whole-repository design analysis. It should not contain repository-wide design conclusions, global refactor plans, global technical debt lists, or architecture judgments.

The purpose is to establish a practical scope boundary so that later onboarding, design learning, and refactor planning remain focused and do not expand to the entire repository.

---

## Trigger

Explain why Scope Discovery was needed.

Possible triggers:

- No module scope was provided.
- The selected scope was the repository root.
- The selected scope appeared too large.
- The repository has unclear or weak module boundaries.
- The conversation repeatedly crossed the current module boundary.
- The user explicitly asked for help choosing a module scope.
- The snapshot produced scope-related warnings.

Current trigger:

```text
<TODO: describe why this scope selection document was created>
```

---

## Repository-Level Snapshot Summary

This section should contain a compact structural summary only.

Do **not** infer whole-repository architecture from this section.

### Snapshot Source

```text
<TODO: path to repo-level snapshot, e.g. .repo-mentor/repo-snapshot.json>
```

### Repository Scale

- Total files: `<TODO>`
- Recognized source files: `<TODO>`
- Directory count: `<TODO>`

### Major Detected Languages

> Language detection is extension-based and approximate.

- `<TODO: language>`: `<TODO: file count>`
- `<TODO: language>`: `<TODO: file count>`

### Top-Level Structure

```text
<TODO: paste compact top-level structure from repo-level snapshot>
```

### Key Config Anchors

> Config anchors indicate possible build, package, or workspace boundaries. They are not design conclusions.

- `<TODO: path>` — `<TODO: location/reason>`
- `<TODO: path>` — `<TODO: location/reason>`

### Scope-Related Warnings

- `<TODO: warning code>`: `<TODO: warning message>`

---

## Candidate Module Scopes

List possible scopes that may be suitable for a focused `repo-mentor` session.

Each candidate should be evaluated using structural evidence and the user's goal, not repository-wide design assumptions.

---

### Candidate 1: `<path/to/module>`

#### Why It May Be a Good Scope

- `<TODO: reason based on structure, file count, config anchors, or user goal>`
- `<TODO: reason>`

#### Risks / Unknowns

- `<TODO: why this scope may be too broad, too narrow, generated-heavy, or coupled to other areas>`
- `<TODO: unknown that needs user confirmation>`

#### Boundary Notes

Inside this scope:

- `<TODO: directories/files considered in scope>`
- `<TODO>`

Outside this scope:

- `<TODO: directories/files treated as external dependencies or boundaries>`
- `<TODO>`

#### Initial Confidence

```text
<TODO: Low / Medium / High>
```

---

### Candidate 2: `<path/to/another/module>`

#### Why It May Be a Good Scope

- `<TODO>`
- `<TODO>`

#### Risks / Unknowns

- `<TODO>`
- `<TODO>`

#### Boundary Notes

Inside this scope:

- `<TODO>`
- `<TODO>`

Outside this scope:

- `<TODO>`
- `<TODO>`

#### Initial Confidence

```text
<TODO: Low / Medium / High>
```

---

### Candidate 3: `<path/to/another/module>`

#### Why It May Be a Good Scope

- `<TODO>`
- `<TODO>`

#### Risks / Unknowns

- `<TODO>`
- `<TODO>`

#### Boundary Notes

Inside this scope:

- `<TODO>`
- `<TODO>`

Outside this scope:

- `<TODO>`
- `<TODO>`

#### Initial Confidence

```text
<TODO: Low / Medium / High>
```

---

## Recommended Initial Scope

```text
<TODO: recommended module scope>
```

---

## Rationale

Explain why this scope is a good starting point.

The rationale must be based on:

- Structural evidence from the snapshot.
- The user's stated goal.
- Manageable size.
- Clear enough boundaries for a focused session.
- Avoidance of generated, vendored, or unrelated areas.

Recommended rationale:

```text
<TODO: explain why this scope should be used first>
```

Avoid statements like:

```text
This repository uses architecture X.
This module is the core of the whole system.
The whole repository should be refactored around this boundary.
```

Unless they are later confirmed through scoped code evidence and user discussion.

---

## Alternative Scopes

If the recommended scope turns out to be too broad, too narrow, or misaligned with the user's goal, consider these alternatives:

1. `<TODO: alternative scope>`
   - When to use: `<TODO>`
   - Why: `<TODO>`

2. `<TODO: alternative scope>`
   - When to use: `<TODO>`
   - Why: `<TODO>`

3. `<TODO: alternative scope>`
   - When to use: `<TODO>`
   - Why: `<TODO>`

---

## Excluded Areas

Areas intentionally not analyzed in this `repo-mentor` session.

Examples:

- `third_party/`
- `vendor/`
- `generated/`
- `build/`
- `dist/`
- unrelated applications
- platform-specific glue outside the current goal
- large generated protocol outputs

Current exclusions:

- `<TODO: path>` — `<TODO: reason>`
- `<TODO: path>` — `<TODO: reason>`

---

## Boundary Rules For This Session

Use these rules to prevent scope creep.

### In Scope

- `<TODO: what repo-mentor may analyze deeply>`
- `<TODO>`

### Boundary-Level Only

These areas may be discussed only as interfaces, dependencies, or integration points.

- `<TODO: external module/path>`
- `<TODO>`

### Out of Scope

These areas should not be analyzed unless the user explicitly updates the scope.

- `<TODO: path>`
- `<TODO>`

---

## Open Questions

Questions that need user confirmation before finalizing or changing the scope.

- `<TODO: question>`
- `<TODO: question>`
- `<TODO: question>`

---

## Decision

Record the current scope decision.

```text
<TODO: selected scope, deferred decision, or pending user confirmation>
```

Decision status:

```text
<TODO: Proposed / Confirmed / Rejected / Needs Revision>
```

---

## Update Log

- `<YYYY-MM-DD>`: Created initial scope selection.
- `<YYYY-MM-DD>`: `<TODO: update summary>`
