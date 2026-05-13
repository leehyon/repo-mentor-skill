# Workflow: Design Digest Distillation

## Purpose

Create or update the module-specific design deep-dive document for a scoped module.

`design-digest.md` captures current understanding of the selected module's design, including design intent, key abstractions, important workflows, engineering trade-offs, hidden assumptions, evidence, and module-specific observations.

It is not the final home for generalized engineering guidance. Reusable takeaways, lessons learned, heuristics, and anti-patterns should be marked as candidates here and then distilled into `engineering-lessons.md` through the Engineering Lessons Distillation workflow.

---

## Relationship To `engineering-lessons.md`

Use `design-digest.md` for:

- module-specific design understanding;
- evidence-heavy technical analysis;
- file-, class-, function-, and workflow-level observations;
- design intent and inferred intent within the selected module;
- module-specific trade-offs and hidden assumptions;
- module-specific takeaways and lessons;
- candidate reusable lessons that need further distillation.

Use `engineering-lessons.md` for:

- reusable engineering knowledge distilled from this module;
- transferable design takeaways;
- lessons learned with applicability conditions;
- design heuristics;
- anti-patterns to avoid;
- guidance for designing or maintaining other modules.

---

## Steps

1. Confirm module scope and module ID.
2. Read module-specific snapshot, if available.
3. Add snapshot-derived facts only under `Evidence From Snapshot`.
4. Separate facts from inferences.
5. Capture confirmed design intent when evidence supports it.
6. Mark inferred design intent explicitly as `Inference`.
7. Identify key abstractions and boundaries.
8. Document important workflows and evidence.
9. Capture engineering trade-offs as they appear in this module.
10. Record hidden assumptions maintainers should respect.
11. Capture module-specific takeaways and lessons.
12. Mark reusable lesson candidates for `engineering-lessons.md`.
13. Put unresolved or weakly supported items in `Open Questions`.

---

## Snapshot Handling Rules

Snapshot data is structural evidence, not a design conclusion.

Acceptable uses:

- use `candidate_entry_points` as reading anchors;
- use `largest_files_by_lines` to identify files worth inspecting;
- use `suspected_generated_or_vendored` to down-weight files during design inference;
- use warnings to revisit scope if needed.

Do not infer directly from snapshot that a module has a specific architecture style, that a large file is a design problem, or that refactoring is required.

---

## Handoff To Engineering Lessons Distillation

When reusable candidates exist, either add links/placeholders in `design-digest.md` or run `engineering-lessons-distillation.md` to update `engineering-lessons.md`.
