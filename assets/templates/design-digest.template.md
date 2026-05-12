# Design Digest

## Scope

- Repository root: `<TODO: repo_root>`
- Module scope: `<TODO: scope>`
- Scope root: `<TODO: scope_root>`
- Scope policy: `module-only`

This document summarizes the current understanding of the scoped module. Inferred design intent must be explicitly marked as inference.

This document is a living design-learning note, not an official source of truth unless the team explicitly promotes it.

---

## Evidence From Snapshot

Use this section for structural evidence from this module's `snapshot.json`.

Do not treat snapshot data as design conclusions.

### Structural Signals

- File count: `<TODO>`
- Recognized source files: `<TODO>`
- Directory count: `<TODO>`
- Main detected languages:
  - `<TODO: language>`: `<TODO: count>`
- Top extensions:
  - `<TODO: extension>`: `<TODO: count>`

### Candidate Reading Anchors

Candidate only; verify through code reading.

- `<TODO: path>` — `<TODO: reason>`
- `<TODO: path>` — `<TODO: reason>`

### Large or Dense Files Worth Inspecting

Large files are not automatically design problems. They may represent core logic, generated tables, protocol definitions, configuration, or legacy accumulation.

- `<TODO: path>` — `<TODO: lines/size>`
- `<TODO: path>` — `<TODO: lines/size>`

### Files To Down-Weight During Design Inference

Generated or vendored candidates should be treated carefully.

- `<TODO: path>` — `<TODO: reason>`
- `<TODO: path>` — `<TODO: reason>`

### Snapshot Warnings

- `<TODO: warning code>`: `<TODO: warning message>`

---

## Current Understanding

Summarize what is currently understood about the module.

Separate facts from inferences.

### Facts

- `<TODO: fact supported by code/snapshot/user confirmation>`
- `<TODO>`

### Inferences

- `Inference:` `<TODO: inferred understanding>`
  - Evidence: `<TODO>`
  - Confidence: `<TODO: Low / Medium / High>`

---

## Design Intent

### Confirmed Intent

Use this only when supported by explicit code structure, naming, comments, tests, user confirmation, or existing design notes.

- `<TODO: confirmed intent>`
  - Evidence: `<TODO>`

### Inferred Intent

Use careful wording.

Example:

```text
Inference: The module likely separates X from Y to reduce coupling between A and B.
```

Current inferred intent:

- `Inference:` `<TODO>`
  - Evidence: `<TODO>`
  - Confidence: `<TODO: Low / Medium / High>`

---

## Key Abstractions

### `<TODO: Abstraction Name>`

- Responsibility: `<TODO>`
- Collaborators: `<TODO>`
- Boundary: `<TODO>`
- Evidence: `<TODO>`
- Why it matters: `<TODO>`

### `<TODO: Abstraction Name>`

- Responsibility: `<TODO>`
- Collaborators: `<TODO>`
- Boundary: `<TODO>`
- Evidence: `<TODO>`
- Why it matters: `<TODO>`

---

## Important Workflows

### `<TODO: Workflow Name>`

- Trigger: `<TODO>`
- Main path: `<TODO>`
- Key files: `<TODO>`
- Boundary interactions: `<TODO>`
- Failure / fallback behavior: `<TODO>`
- Evidence: `<TODO>`

### `<TODO: Workflow Name>`

- Trigger: `<TODO>`
- Main path: `<TODO>`
- Key files: `<TODO>`
- Boundary interactions: `<TODO>`
- Failure / fallback behavior: `<TODO>`
- Evidence: `<TODO>`

---

## Engineering Trade-offs

### `<TODO: Trade-off>`

- Context: `<TODO>`
- Chosen approach: `<TODO>`
- Benefit: `<TODO>`
- Cost: `<TODO>`
- Evidence: `<TODO>`
- When this approach is reusable: `<TODO>`
- When to avoid it: `<TODO>`

---

## Takeaways

Reusable lessons from good design. Each takeaway should be written as a transferable engineering principle.

### Takeaway: `<TODO: short principle>`

- What the module does well: `<TODO>`
- Why it works: `<TODO>`
- Where it appears: `<TODO>`
- How to reuse this idea elsewhere: `<TODO>`

### Takeaway: `<TODO: short principle>`

- What the module does well: `<TODO>`
- Why it works: `<TODO>`
- Where it appears: `<TODO>`
- How to reuse this idea elsewhere: `<TODO>`

---

## Lessons Learned

Lessons from problematic, risky, or confusing design.

Important: Lessons are not automatically refactor requests.

### Lesson: `<TODO: short lesson>`

- Observed issue: `<TODO>`
- Why it matters: `<TODO>`
- Evidence: `<TODO>`
- Impact on maintainability: `<TODO>`
- Possible future direction: `<TODO>`

### Lesson: `<TODO: short lesson>`

- Observed issue: `<TODO>`
- Why it matters: `<TODO>`
- Evidence: `<TODO>`
- Impact on maintainability: `<TODO>`
- Possible future direction: `<TODO>`

---

## Hidden Assumptions

Implicit constraints that maintainers should respect.

Examples:

- initialization order
- threading model
- ownership model
- lifecycle assumptions
- hardware/platform assumptions
- timing assumptions
- error handling assumptions

Current hidden assumptions:

- `<TODO: assumption>`
  - Evidence: `<TODO>`
  - Risk if violated: `<TODO>`

- `<TODO: assumption>`
  - Evidence: `<TODO>`
  - Risk if violated: `<TODO>`

---

## Open Questions

Questions that still need evidence or user confirmation.

- `<TODO: question>`
- `<TODO: question>`
- `<TODO: question>`

---

## Update Log

- `<YYYY-MM-DD>`: Created initial design digest.
- `<YYYY-MM-DD>`: `<TODO: update summary>`
