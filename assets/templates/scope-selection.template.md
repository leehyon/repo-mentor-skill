# Scope Selection

## Purpose

This document helps choose or refine a manageable module scope for `repo-mentor`.

It is **not** a whole-repository design analysis. It should not contain whole-repository architecture conclusions, global technical debt lists, or global refactor plans.

---

## Trigger

Explain why Scope Discovery was needed.

Possible triggers:

- No module scope was provided.
- The selected scope was the repository root.
- The selected scope appeared too large.
- The repository has unclear or weak module boundaries.
- The conversation repeatedly crossed the current scope boundary.
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

- Snapshot source: `<TODO: .repo-mentor/repo-snapshot.json>`
- Total files: `<TODO>`
- Recognized source files: `<TODO>`
- Directory count: `<TODO>`
- Major detected languages: `<TODO>`
- Key config anchors: `<TODO>`
- Scope-related warnings: `<TODO>`

### Top-Level Structure

```text
<TODO: compact top-level structure>
```

---

## Candidate Module Scopes

### Candidate: `<path/to/module>`

#### Why It May Be A Good Scope

- `<TODO: reason based on structure, file count, config anchors, or user goal>`

#### Risks / Unknowns

- `<TODO: why this scope may be too broad, too narrow, generated-heavy, or coupled>`

#### Boundary Notes

Inside scope:

- `<TODO>`

Boundary-level only:

- `<TODO>`

Out of scope:

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

## Rationale

<TODO: explain why this scope is the best starting point based on structural evidence and user goal>

## Alternative Scopes

1. `<TODO: alternative scope>`
   - When to use: `<TODO>`
   - Why: `<TODO>`

## Excluded Areas

- `<TODO: path>` — `<TODO: reason>`

## Boundary Rules For This Session

### In Scope

- `<TODO>`

### Boundary-Level Only

- `<TODO>`

### Out Of Scope

- `<TODO>`

## Open Questions

- `<TODO>`

## Decision

```text
<TODO: Proposed / Confirmed / Rejected / Needs Revision>
```

## Update Log

- `<YYYY-MM-DD>`: Created initial scope selection.
