# Scoped Codebase Mentoring

`repo-mentor` is an Agent Skill for learning, understanding, and distilling engineering knowledge from a scoped module in an unfamiliar codebase.

It helps engineers:

- understand a selected module without expanding to the entire repository;
- ask code and design questions through conversation;
- build concise onboarding notes;
- create a module-specific design deep dive;
- extract reusable engineering lessons, takeaways, heuristics, and anti-patterns;
- create safe refactor plans only when refactoring is explicitly discussed.

The core idea is:

```text
understand the module -> explain the design -> distill reusable lessons -> evolve safely
```

## What This Skill Produces

When used on a target repository, `repo-mentor` writes its outputs under the repository root:

```text
.repo-mentor/
├── index.md                         # optional, recommended when multiple modules are analyzed
├── scope-selection.md               # optional, repo-level, only when Scope Discovery is used
├── repo-snapshot.json               # optional, repo-level, only for Scope Discovery
└── modules/
    └── <module-id>/
        ├── snapshot.json
        ├── onboarding.md
        ├── design-digest.md
        ├── engineering-lessons.md
        └── refactor-plan.md         # only when refactor-related discussion is triggered
```

## How To Interact

Use short, direct prompts. The skill carries the workflow.

### Understand A Module

```text
Use the repo-mentor skill to help me understand the current design of the `src/power_manager` module.
```

### Explore First, Summarize Later

```text
Use the repo-mentor skill in conversation-first mode for the `src/power_manager` module; do not update files until I ask.
```

### Ask A Design Question

```text
Use the repo-mentor skill to explain why `src/power_manager` separates event dispatching from state transitions.
```

### Summarize Into Notes

```text
Use the repo-mentor skill to summarize our discussion into repo-mentor notes for the `src/power_manager` module.
```

### Extract Reusable Lessons

```text
Use the repo-mentor skill to extract reusable engineering lessons from our discussion about `src/power_manager`.
```

### Plan A Refactor

```text
Use the repo-mentor skill to create a safe refactor plan for the state machine code in `src/power_manager`.
```

### Choose A Scope

```text
Use the repo-mentor skill to help me choose a manageable module scope for this repository.
```

## Output Routing

- Newcomer orientation -> `onboarding.md`
- Module-specific design details -> `design-digest.md`
- Reusable engineering lessons -> `engineering-lessons.md`
- Refactoring discussion -> `refactor-plan.md`
- Scope choice -> `scope-selection.md`
