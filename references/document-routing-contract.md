# Document Routing Contract

## Purpose

This contract defines where `repo-mentor` should write information when maintaining living Markdown notes.

---

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

Do not mix outputs from different modules in the same directory.

---

## Routing Rules

### Route To `onboarding.md`

Use for information that helps a newcomer quickly get oriented:

- module scope
- concise responsibility summary
- practical mental model
- key concepts
- reading path
- top-level structure
- common newcomer pitfalls
- links to deeper design notes

Keep this file concise.

Do not put deep technical details, long workflow analysis, reusable engineering lessons, or refactor plans here.

---

### Route To `design-digest.md`

Use for module-specific design learning and deep technical understanding:

- current understanding
- confirmed design intent
- inferred design intent
- key abstractions
- important workflows
- engineering trade-offs
- hidden assumptions
- module-specific observations
- module-specific takeaways and lessons
- evidence
- open questions

Do not overload this file with generalized guidance. Distill reusable principles into `engineering-lessons.md`.

---

### Route To `engineering-lessons.md`

Use for reusable engineering knowledge distilled from the scoped module:

- reusable design takeaways
- lessons learned
- design heuristics
- anti-patterns to avoid
- applicability conditions
- when to reuse an idea
- when not to reuse an idea
- links back to evidence in `design-digest.md` and code

Do not put module-specific implementation details here.

Do not present lessons as universal best practices. Preserve source context and applicability.

---

### Route To `refactor-plan.md`

Use only when refactor-related discussion exists:

- refactor triggers
- observed pain points
- design smells
- what should be preserved
- refactor goals
- non-goals
- proposed safe steps
- risks
- validation strategy
- rollback strategy
- migration notes

Do not create this file from snapshot data alone.

---

### Route To `scope-selection.md`

Use only during Scope Discovery:

- why scope discovery was needed
- repository-level structural summary
- candidate module scopes
- recommended initial scope
- excluded areas
- boundary rules
- scope-related open questions

Do not include whole-repository design conclusions.

---

### Route To `index.md`

Use when multiple modules are analyzed.

May include:

- module scope
- module ID
- note directory
- status
- last updated date

Do not turn `index.md` into architecture documentation.

---

## Uncertainty Routing

If information is uncertain, do not write it as a conclusion.

Use:

- `Open Questions` in the relevant document
- explicit `Inference:` labels
- confidence markers such as `Low`, `Medium`, or `High`

---

## Promotion And Distillation Rules

Promote information to `onboarding.md` only when it is stable, beginner-relevant, and useful for orientation.

Keep detailed module-specific explanations in `design-digest.md`.

Distill reusable engineering guidance into `engineering-lessons.md` only when it can be expressed with source context and applicability conditions.

Move actionable refactor content into `refactor-plan.md` only when the user has triggered refactor planning.
