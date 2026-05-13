# Workflow: Conversation-First Learning

## Purpose

Allow the user to ask scoped code questions first, then summarize and update repo-mentor notes later.

This workflow is useful when the user is still exploring the module and does not want documents to be generated or updated too early.

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

During conversation-first mode, `repo-mentor` should:

1. Stay within the selected module scope.
2. Answer the user's code questions directly.
3. Separate facts from inferences.
4. Mark uncertainty explicitly.
5. Capture module-specific observations for possible `design-digest.md` updates.
6. Capture reusable takeaways and lessons for possible `engineering-lessons.md` updates.
7. Track open questions.
8. Track possible refactor topics without turning them into a refactor plan unless the user asks.
9. Ask for missing code context only when needed.
10. Avoid expanding to the whole repository.

---

## Suggested Answer Shape

When useful, structure answers like this:

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

## Lessons / Risks

- <candidate module-specific lesson or risk, if any>

## Open Questions

- <what still needs confirmation>
```

Do not force every answer into this exact structure when the user's question is small, but preserve the distinction between facts, inference, uncertainty, module-specific observations, and reusable lessons.

---

## Conversation Learning Buffer

Maintain an implicit learning buffer in the conversation.

The buffer should contain:

- Facts observed
- Inferences
- Module-specific observations
- Candidate reusable engineering lessons
- Hidden assumptions
- Open questions
- Possible refactor topics

This buffer does not need to be written to a file unless the user asks.

---

## Deferred Summary Trigger

When the user later says something like:

- summarize this
- update the notes
- generate onboarding
- update design-digest
- extract engineering lessons
- distill takeaways and lessons
- save this into repo-mentor docs
- persist our discussion

then summarize the conversation into the appropriate repo-mentor documents.

---

## Document Routing On Summary

When summarizing:

### Route To `onboarding.md`

Put beginner-relevant stable knowledge into:

```text
.repo-mentor/modules/<module-id>/onboarding.md
```

### Route To `design-digest.md`

Put module-specific design-learning content into:

```text
.repo-mentor/modules/<module-id>/design-digest.md
```

Examples:

- current understanding
- design intent
- key abstractions
- important workflows
- engineering trade-offs in this module
- module-specific observations
- hidden assumptions
- open questions

### Route To `engineering-lessons.md`

Put reusable engineering knowledge into:

```text
.repo-mentor/modules/<module-id>/engineering-lessons.md
```

Examples:

- reusable design takeaways
- lessons learned
- design heuristics
- anti-patterns
- applicability conditions
- when not to reuse an idea
- links back to `design-digest.md`

### Route To `refactor-plan.md`

Create or update:

```text
.repo-mentor/modules/<module-id>/refactor-plan.md
```

only if the conversation included refactoring, technical debt, maintainability issues, design smells, or architecture evolution.

### Route To `scope-selection.md`

Update:

```text
.repo-mentor/scope-selection.md
```

only if the conversation was about choosing or revising scope.

---

## Important Summary Rules

Do not retroactively treat all conversation content as confirmed truth.

Classify summarized content as:

- Confirmed facts
- Inferences
- Module-specific observations
- Reusable engineering lessons
- Hidden assumptions
- Open questions
- Refactor topics, only when triggered

If confidence is low, either mark it explicitly or keep the item in `Open Questions`.

---

## Non-Goals

Do not:

- Force document generation during exploration.
- Expand beyond the module scope.
- Treat provisional conversation ideas as confirmed design intent.
- Create a refactor plan unless refactor-related discussion was triggered.
- Move every technical detail into onboarding.
- Present reusable lessons as universal best practices without applicability conditions.

---

## Completion Criteria

This workflow is complete when the user asks to summarize and the conversation has been distilled into concise, maintainable notes without losing uncertainty or over-promoting tentative conclusions.
