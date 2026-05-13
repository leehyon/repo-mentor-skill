# Workflow: Engineering Lessons Distillation

## Purpose

Distill reusable engineering knowledge from module-specific design understanding.

This workflow turns observations from `design-digest.md` and conversation into `engineering-lessons.md`.

The goal is not to create universal best practices. The goal is to capture applicability-aware engineering lessons that can inform future module design and maintenance.

---

## When To Use

Use this workflow when:

- `design-digest.md` contains takeaways or lessons that may be reusable;
- the user asks to extract lessons, best practices, or reusable design guidance;
- a conversation reveals a transferable pattern, heuristic, or anti-pattern;
- the user asks to summarize technical learning beyond the current module.

---

## Steps

1. Review module-specific observations in `design-digest.md`.
2. Identify which observations are reusable beyond the current module.
3. Convert good design observations into reusable takeaways.
4. Convert confusing, risky, or costly observations into lessons learned.
5. Extract design heuristics where appropriate.
6. Extract anti-patterns only when evidence supports them.
7. Preserve source context and evidence.
8. Add applicability conditions: when to use, adapt, or avoid.
9. Link back to `design-digest.md` and source files.
10. Keep module-specific implementation details out of `engineering-lessons.md`.

---

## Distillation Rules

Each reusable lesson should answer:

- What is the reusable principle?
- Where did it come from?
- Why does it matter?
- How can it be reused?
- When does it apply?
- When should it not be reused?
- What evidence supports it?

---

## Do Not

- Present a lesson as a universal best practice without conditions.
- Copy long module-specific implementation details from `design-digest.md`.
- Generalize from weak evidence without marking uncertainty.
- Turn lessons into refactor plans unless refactor planning was triggered.
