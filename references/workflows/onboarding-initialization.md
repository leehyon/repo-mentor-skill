# Workflow: Onboarding Initialization

## Purpose

Create or update a concise onboarding note for a scoped module.

The goal is to help a newcomer build a practical mental model quickly.

---

## Inputs

- module-specific `snapshot.json`
- user goal
- known files or workflows of interest
- existing `onboarding.md`, if any
- relevant confirmed facts from conversation

---

## Output

Create or update:

```text
.repo-mentor/modules/<module-id>/onboarding.md
```

Use:

```text
assets/templates/onboarding.template.md
```

---

## Steps

1. Fill module scope information.
2. Add compact module snapshot facts.
3. Write a cautious summary of what the module appears to do.
4. Define the simplest useful mental model, if supported.
5. Identify key beginner concepts.
6. Provide a recommended reading path.
7. Include compact top-level structure.
8. Add stable newcomer pitfalls.
9. Link to deeper sections in `design-digest.md`.
10. Add unresolved items to `Open Questions`.

---

## Style Rules

Use cautious language:

- `appears to`
- `based on current evidence`
- `to be confirmed`

Avoid:

- deep implementation details
- unconfirmed design intent
- refactor plans
- whole-repository claims

---

## Completion Criteria

The document should let a newcomer understand where to start without needing to read detailed design analysis first.
