# Document Routing Contract

## Output Locations

Module-specific outputs:

```text
.repo-mentor/modules/<module-id>/onboarding.md
.repo-mentor/modules/<module-id>/design-digest.md
.repo-mentor/modules/<module-id>/engineering-lessons.md
.repo-mentor/modules/<module-id>/refactor-plan.md
.repo-mentor/modules/<module-id>/snapshot.json
```

Repo-level optional outputs:

```text
.repo-mentor/scope-selection.md
.repo-mentor/repo-snapshot.json
.repo-mentor/index.md
```

## Routing Rules

- `onboarding.md`: newcomer orientation, concise mental model, key concepts, reading path.
- `design-digest.md`: module-specific design intent, abstractions, workflows, trade-offs, hidden assumptions, evidence, module-specific observations.
- `engineering-lessons.md`: reusable engineering takeaways, lessons, heuristics, anti-patterns, applicability conditions, links to evidence.
- `refactor-plan.md`: only when refactor-related discussion exists.
- `scope-selection.md`: only during Scope Discovery.

If uncertain, write to `Open Questions` or mark as `Inference` with confidence.
