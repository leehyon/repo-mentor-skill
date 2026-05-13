# Workflow: Conversation-First Learning

## Purpose

Allow the user to ask scoped code questions first, then summarize and update repo-mentor notes later.

The goal is:

```text
explore -> clarify -> distill -> persist
```

---

## When To Use

Use this workflow when the user says or implies:

- I want to ask questions first.
- Let's discuss the code before generating notes.
- Don't update documents yet.
- I'll ask you to summarize later.
- Let's explore this module interactively.
- Use conversation-first mode.

---

## Behavior During Conversation

During exploration, `repo-mentor` should:

1. Stay within the selected module scope.
2. Answer the user's code questions directly.
3. Separate facts from inferences.
4. Mark uncertainty explicitly.
5. Capture module-specific observations for possible `design-digest.md` updates.
6. Capture reusable takeaways and lessons for possible `engineering-lessons.md` updates.
7. Track open questions.
8. Track possible refactor topics without creating a refactor plan unless asked.
9. Ask for missing code context only when needed.
10. Avoid expanding to the whole repository.

---

## Suggested Answer Shape

Use this shape when helpful:

```markdown
## Short Answer

<TODO: direct answer>

## Evidence

- `<path>`: <observed fact>

## Inference

- Inference: <careful inferred design intent or trade-off>

## Module-Specific Observations

- <candidate item for design-digest.md>

## Reusable Engineering Lessons

- <candidate item for engineering-lessons.md>

## Open Questions

- <what still needs confirmation>
```

Do not force every small answer into this structure, but preserve fact/inference/uncertainty separation.

---

## Deferred Summary Trigger

When the user later asks to summarize, update notes, extract lessons, or persist the discussion, summarize into the correct documents.

### Route To `onboarding.md`

Beginner-relevant stable knowledge.

### Route To `design-digest.md`

Module-specific design-learning content.

### Route To `engineering-lessons.md`

Reusable engineering guidance.

### Route To `refactor-plan.md`

Only if the conversation included refactoring, technical debt, maintainability issues, design smells, or architecture evolution.

---

## Important Summary Rules

Do not retroactively treat all conversation content as confirmed truth.

Classify summarized content as:

- confirmed facts;
- inferences;
- module-specific observations;
- reusable engineering lessons;
- hidden assumptions;
- open questions;
- refactor topics only when triggered.
