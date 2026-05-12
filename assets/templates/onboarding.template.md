# Onboarding

## Module Scope

- Repository root: `<TODO: repo_root>`
- Module scope: `<TODO: scope>`
- Scope root: `<TODO: scope_root>`
- Scope policy: `module-only`

This onboarding note is limited to the selected module scope. Cross-module behavior should be described only at boundary level unless the scope is explicitly updated.

---

## Module Snapshot

Use facts from this module's `snapshot.json` only as structural evidence, not as design conclusions.

- Total files: `<TODO>`
- Recognized source files: `<TODO>`
- Directory count: `<TODO>`
- Main detected languages:
  - `<TODO: language>`: `<TODO: count>`
  - `<TODO: language>`: `<TODO: count>`
- Key config anchors:
  - `<TODO: path>` — `<TODO: location/reason>`

Notes:

- Language detection is extension-based and approximate.
- Candidate entry points are heuristic anchors, not confirmed runtime entry points.
- Documentation, comments, and tests are not treated as authoritative design truth by default.

---

## What This Module Appears To Do

Write a short, beginner-friendly summary of the module.

Use careful wording:

- `appears to`
- `based on current evidence`
- `to be confirmed`

Summary:

```text
<TODO: concise module responsibility summary>
```

Avoid overstating design intent or making whole-repository claims.

---

## Mental Model

Explain the simplest useful mental model for understanding the module.

Examples:

- pipeline
- state machine
- adapter layer
- dispatcher
- protocol parser
- orchestration layer
- hardware abstraction boundary

Current mental model:

```text
<TODO: describe the practical mental model>
```

Evidence:

- `<TODO: file/path/conversation evidence>`
- `<TODO>`

---

## Key Concepts

List stable concepts a newcomer should learn first.

### `<TODO: Concept Name>`

- What it means: `<TODO>`
- Why it matters: `<TODO>`
- Where to inspect next: `<TODO: file/path/section>`

### `<TODO: Concept Name>`

- What it means: `<TODO>`
- Why it matters: `<TODO>`
- Where to inspect next: `<TODO: file/path/section>`

---

## How to Start Reading

Recommended reading path for a newcomer.

> These are candidate reading anchors and should be verified through code reading.

1. `<TODO: candidate or confirmed entry file>`
   - Why: `<TODO>`
   - Status: `<TODO: Candidate / Confirmed>`

2. `<TODO: next file or directory>`
   - Why: `<TODO>`
   - Status: `<TODO: Candidate / Confirmed>`

3. `<TODO: next file or directory>`
   - Why: `<TODO>`
   - Status: `<TODO: Candidate / Confirmed>`

---

## Top-Level Structure

Compact structure from the scoped snapshot.

Do not infer architecture solely from directory names.

```text
<TODO: paste compact directory structure from snapshot.json>
```

---

## Common Newcomer Pitfalls

Only include stable pitfalls observed through code evidence or user discussion.

Examples:

- misleading names
- generated files
- implicit initialization order
- cross-module dependency boundaries
- large files requiring careful reading

Current pitfalls:

- `<TODO: pitfall>`
  - Why it matters: `<TODO>`
  - How to avoid confusion: `<TODO>`

- `<TODO: pitfall>`
  - Why it matters: `<TODO>`
  - How to avoid confusion: `<TODO>`

---

## Deeper Reading

Use this section to point newcomers to deeper notes in `design-digest.md`.

- See `design-digest.md#current-understanding` for the current design understanding.
- See `design-digest.md#key-abstractions` for important abstractions.
- See `design-digest.md#important-workflows` for detailed workflows.
- See `design-digest.md#engineering-trade-offs` for trade-offs.
- See `design-digest.md#hidden-assumptions` for implicit assumptions.

Additional links:

- `<TODO: section or file>`
- `<TODO>`

---

## Open Questions

Questions not yet resolved.

- `<TODO: question>`
- `<TODO: question>`
- `<TODO: question>`

---

## Update Log

- `<YYYY-MM-DD>`: Created initial onboarding note.
- `<YYYY-MM-DD>`: `<TODO: update summary>`
