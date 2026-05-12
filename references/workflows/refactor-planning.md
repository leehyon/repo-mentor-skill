# Workflow: Refactor Planning

## Purpose

Create or update a safe, scoped refactor plan only when refactor-related discussion is triggered by the user.

---

## Triggers

Use this workflow when the user discusses:

- refactoring
- technical debt
- maintainability issues
- design smells
- architecture evolution
- risky or confusing design that may become actionable

Do not trigger this workflow from snapshot data alone.

---

## Inputs

- user refactor question or intent
- existing `design-digest.md`
- scoped code evidence
- observed pain points
- known constraints
- existing `refactor-plan.md`, if any

---

## Output

Create or update:

```text
.repo-mentor/modules/<module-id>/refactor-plan.md
```

Use:

```text
assets/templates/refactor-plan.template.md
```

---

## Steps

1. Record the trigger.
2. Confirm scope and out-of-scope areas.
3. List observed pain points with evidence.
4. Identify design smells only when evidence supports them.
5. Record what should be preserved.
6. Define refactor goals.
7. Define non-goals to prevent scope creep.
8. Propose small, reversible steps.
9. Assess risks.
10. Define validation strategy.
11. Define rollback strategy.
12. Record migration notes if needed.
13. Put unresolved issues in `Open Questions`.

---

## Safety Rules

- Preserve good existing design choices.
- Prefer behavior-preserving changes first.
- Avoid large rewrites.
- Avoid cross-scope changes unless the user explicitly expands scope.
- Include validation before structural change.
- Include rollback strategy.
- Do not recommend refactoring solely because a file is large.

---

## Completion Criteria

The plan should be safe enough that a maintainer can execute it incrementally while preserving existing behavior.
