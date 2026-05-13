# Workflow: Design Digest Distillation

## Purpose

Create or update the module-specific design deep-dive document for a scoped module.

`design-digest.md` captures the current understanding of the selected module's design, including design intent, key abstractions, important workflows, engineering trade-offs, hidden assumptions, evidence, and module-specific observations.

It is not the final home for generalized engineering guidance. Reusable takeaways, lessons learned, heuristics, and anti-patterns should be marked as candidates here and then distilled into `engineering-lessons.md` through the Engineering Lessons Distillation workflow.

---

## Relationship To `engineering-lessons.md`

Use `design-digest.md` for:

- Module-specific design understanding.
- Evidence-heavy technical analysis.
- File-, class-, function-, and workflow-level observations.
- Design intent and inferred intent within the selected module.
- Module-specific trade-offs and hidden assumptions.
- Module-specific takeaways and lessons.
- Candidate reusable lessons that need further distillation.

Use `engineering-lessons.md` for:

- Reusable engineering knowledge distilled from this module.
- Transferable design takeaways.
- Lessons learned with applicability conditions.
- Design heuristics.
- Anti-patterns to avoid.
- Guidance for designing or maintaining other modules.

Do not duplicate long module-specific details in `engineering-lessons.md`. Link back to `design-digest.md` instead.

---

## When To Use

Use this workflow when:

- The user asks for module design understanding.
- The user asks why a module is structured in a certain way.
- The user asks detailed technical questions whose answers should be preserved.
- A scoped snapshot exists and should be converted into design evidence.
- Conversation-first exploration should be summarized into module-specific design notes.
- Existing `design-digest.md` needs to be updated with new evidence or corrected understanding.

---

## Inputs

- Module-specific `snapshot.json`:

```text
.repo-mentor/modules/<module-id>/snapshot.json
```

- Scoped code evidence.
- User questions and answers.
- Existing `design-digest.md`, if any.
- Existing `engineering-lessons.md`, if any.
- Confirmed observations from conversation.
- Open questions from prior notes.

---

## Primary Output

Create or update:

```text
.repo-mentor/modules/<module-id>/design-digest.md
```

Use:

```text
assets/templates/design-digest.template.md
```

---

## Related Output

When reusable engineering lessons are identified, mark them as candidates in `design-digest.md` and then use:

```text
references/workflows/engineering-lessons-distillation.md
```

to create or update:

```text
.repo-mentor/modules/<module-id>/engineering-lessons.md
```

Use:

```text
assets/templates/engineering-lessons.template.md
```

---

## Steps

1. Confirm module scope and module ID.
2. Read the module-specific snapshot, if available.
3. Add snapshot-derived facts only under `Evidence From Snapshot`.
4. Separate facts from inferences.
5. Capture confirmed design intent when evidence supports it.
6. Mark inferred design intent explicitly as `Inference`.
7. Identify key abstractions and their module boundaries.
8. Document important workflows and their evidence.
9. Capture engineering trade-offs as they appear in this module.
10. Record hidden assumptions maintainers should respect.
11. Capture module-specific takeaways and lessons.
12. Mark reusable lesson candidates for `engineering-lessons.md`.
13. Link to existing `engineering-lessons.md` entries when reusable lessons have already been distilled.
14. Put unresolved or weakly supported items in `Open Questions`.
15. Update the `Update Log`.

---

## Evidence Requirements

Every important claim should have at least one evidence source:

- File path.
- Symbol name.
- Snapshot field.
- User confirmation.
- Prior conversation result.
- Existing repo-mentor note.

If evidence is weak, mark confidence as `Low` or keep the item in `Open Questions`.

---

## Snapshot Handling Rules

Snapshot data is structural evidence, not a design conclusion.

Acceptable uses:

- Use `candidate_entry_points` as reading anchors.
- Use `largest_files_by_lines` to identify files worth inspecting.
- Use `suspected_generated_or_vendored` to down-weight files during design inference.
- Use `directory_structure` as structural context.
- Use warnings to revisit scope if needed.

Do not infer directly from snapshot that:

- The module has a specific architecture style.
- A large file is a design problem.
- A directory name proves a design pattern.
- Refactoring is required.

---

## Module-Specific Takeaway Rules

In `design-digest.md`, takeaways should remain tied to the module context.

Good format:

```markdown
### Module-Specific Takeaway: `<short observation>`

- Observation: `<what appears to work well in this module>`
- Why it matters in this module: `<local design value>`
- Evidence: `<file/path/symbol>`
- Reusable lesson candidate: `<yes/no/link to engineering-lessons.md>`
```

Do not fully generalize the takeaway here. If it is reusable, pass it to `engineering-lessons.md`.

---

## Module-Specific Lesson Rules

In `design-digest.md`, lessons should describe what is confusing, risky, or costly in this module.

Good format:

```markdown
### Module-Specific Lesson: `<short observation>`

- Observed issue: `<what is confusing, risky, or costly>`
- Why it matters in this module: `<local impact>`
- Evidence: `<file/path/symbol>`
- Possible future direction: `<optional>`
- Reusable lesson candidate: `<yes/no/link to engineering-lessons.md>`
```

A module-specific lesson is not automatically a refactor request.

If the user asks for refactoring or maintainability planning, route actionable content to `refactor-plan.md`.

---

## Reusable Lesson Candidate Criteria

Mark an observation as a reusable lesson candidate when it appears to have value beyond the current module.

Examples:

- A design pattern that reduces coupling.
- A boundary that makes testing easier.
- A lifecycle pattern that avoids resource leaks.
- A confusing abstraction that other modules should avoid.
- A trade-off that is useful only under certain constraints.
- A hidden assumption that should be made explicit in future designs.

A candidate should include:

- Source context.
- Evidence.
- Why it may be reusable.
- What applicability questions remain.

---

## Handoff To Engineering Lessons Distillation

When reusable candidates exist, either:

1. Add links/placeholders in `design-digest.md` under `Links To Distilled Engineering Lessons`, or
2. Run `engineering-lessons-distillation.md` to update `engineering-lessons.md`.

Do not leave reusable lessons only buried inside design details if the user asked for technical distillation.

---

## Do Not

Do not:

- Treat README/docs/tests/comments as authoritative design truth by default.
- Present inferred intent as confirmed fact.
- Expand beyond the selected module scope.
- Turn module-specific observations into universal best practices.
- Duplicate long implementation details in `engineering-lessons.md`.
- Create refactor plans unless refactor-related discussion was triggered.
- Treat snapshot data alone as evidence of design quality.

---

## Completion Criteria

This workflow is complete when `design-digest.md` contains a clear, evidence-backed, module-specific design understanding and any reusable lesson candidates are clearly marked for `engineering-lessons.md`.
