# Workflow: Design Digest Distillation

## Purpose

Create or update the core design-learning document for a scoped module.

`design-digest.md` distills design intent, engineering trade-offs, takeaways, lessons learned, and hidden assumptions.

---

## Inputs

- module-specific `snapshot.json`
- scoped code evidence
- user questions and answers
- existing `design-digest.md`, if any
- confirmed observations from conversation

---

## Output

Create or update:

```text
.repo-mentor/modules/<module-id>/design-digest.md
```

Use:

```text
assets/templates/design-digest.template.md
```

---

## Steps

1. Record module scope.
2. Add snapshot evidence under `Evidence From Snapshot`.
3. Separate facts from inferences.
4. Capture confirmed design intent when evidence supports it.
5. Mark inferred design intent explicitly as `Inference`.
6. Identify key abstractions and their boundaries.
7. Document important workflows.
8. Extract engineering trade-offs.
9. Convert good design observations into transferable takeaways.
10. Convert confusing or risky observations into lessons learned.
11. Record hidden assumptions.
12. Put unresolved items in `Open Questions`.

---

## Evidence Requirements

Every important claim should have at least one evidence source:

- file path
- symbol name
- snapshot field
- user confirmation
- prior conversation result

If evidence is weak, mark confidence as `Low` or keep it as an open question.

---

## Takeaway Rules

Takeaways should be reusable engineering principles, not just praise.

Example:

```text
Takeaway: Isolate protocol parsing from business decisions so transport changes do not affect policy logic.
```

---

## Lesson Rules

Lessons are not automatically refactor requests.

A lesson may become refactor input only when the user asks for refactoring or maintainability planning.

---

## Completion Criteria

The document should help maintainers understand not only what the module does, but also what design experience can be learned from it.
