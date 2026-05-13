# Onboarding

## Module Scope

- Repository root: `<TODO: repo_root>`
- Module scope: `<TODO: scope>`
- Module ID: `<TODO: module-id>`
- Scope policy: `module-only`

This onboarding note is limited to the selected module scope. Cross-module behavior should be described only at boundary level unless the scope is explicitly updated.

---

## Module Snapshot

Use facts from this module's `snapshot.json` only as structural evidence, not as design conclusions.

- Total files: `<TODO>`
- Recognized source files: `<TODO>`
- Directory count: `<TODO>`
- Main detected languages: `<TODO>`
- Key config anchors: `<TODO>`

Notes:

- Language detection is extension-based and approximate.
- Candidate entry points are heuristic anchors, not confirmed runtime entry points.
- Documentation, comments, and tests are not treated as authoritative design truth by default.

---

## What This Module Appears To Do

<TODO: concise module responsibility summary using cautious wording>

Use careful wording:

- `appears to`
- `based on current evidence`
- `to be confirmed`

---

## Mental Model

<TODO: the simplest useful mental model for understanding the module>

Examples:

- pipeline
- state machine
- adapter layer
- dispatcher
- protocol parser
- orchestration layer
- hardware abstraction boundary

Evidence:

- `<TODO: file/path/conversation evidence>`

---

## Key Concepts

### `<Concept Name>`

- What it means: `<TODO>`
- Why it matters: `<TODO>`
- Where to inspect next: `<TODO>`

---

## How To Start Reading

Recommended reading path for a newcomer.

> These are candidate reading anchors and should be verified through code reading.

1. `<TODO: file/path>`
   - Why: `<TODO>`
   - Status: `<Candidate / Confirmed>`

2. `<TODO: file/path>`
   - Why: `<TODO>`
   - Status: `<Candidate / Confirmed>`

---

## Top-Level Structure

```text
<TODO: compact structure from snapshot>
```

Do not infer architecture solely from directory names.

---

## Common Newcomer Pitfalls

Only include stable pitfalls observed through code evidence or user discussion.

- `<TODO: pitfall>`
  - Why it matters: `<TODO>`
  - How to avoid confusion: `<TODO>`

---

## Deeper Reading

- `design-digest.md` for module-specific design details.
- `engineering-lessons.md` for reusable engineering lessons.
- `refactor-plan.md` if refactoring has been discussed.

## Open Questions

- `<TODO>`

## Update Log

- `<YYYY-MM-DD>`: Created initial onboarding note.
