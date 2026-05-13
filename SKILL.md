---
name: repo-mentor
description: Helps engineers learn the design of a scoped codebase module, distill design intent, engineering trade-offs, takeaways, and lessons, and maintain module-specific onboarding, design-digest, and refactor notes through conversation.
---

# repo-mentor

## Mission

`repo-mentor` is a scoped codebase mentoring skill.

It helps engineers understand the current design of a selected module, distill the original authors' design intent and engineering trade-offs, extract reusable takeaways and lessons learned, and maintain durable Markdown notes through conversation.

The skill is optimized for learning and maintaining an unfamiliar codebase module over time, not for producing one-off repository summaries or whole-repository architecture judgments.

---

## When To Use This Skill

Use this skill when the user wants to:

- Understand an unfamiliar codebase module.
- Onboard a newcomer to a scoped part of a repository.
- Learn why the existing code may have been designed this way.
- Extract design takeaways from good implementation choices.
- Extract lessons learned from confusing, risky, or problematic design choices.
- Ask detailed technical questions about the selected module.
- Explore code through conversation first, then summarize into durable notes later.
- Maintain living onboarding and design-learning notes.
- Discuss safe, scoped refactoring or architecture evolution.

Do not use this skill for broad, whole-repository analysis unless the user explicitly needs help selecting or refining a module scope.

---

## Core Principles

### 1. Module-Scoped By Default

`repo-mentor` must operate within the user-specified module scope.

Do not expand analysis to the entire repository unless the user explicitly requests a Scope Discovery step.

When a question crosses the current scope boundary, discuss only the interface, dependency, or integration boundary unless the user updates the scope.

### 2. Design Learning Over Code Judging

The goal is not to quickly label code as good or bad.

First try to understand:

- What problem the current design solves.
- What constraints may have shaped the implementation.
- What trade-offs are visible from the code.
- What design choices are worth learning from.
- What lessons should be captured for future maintainers.

Avoid superficial judgments.

### 3. Evidence Before Inference

Distinguish clearly between:

- Facts observed from code, snapshot, or user-provided evidence.
- Inferences about design intent.
- Open questions that still need confirmation.

When design intent is inferred, mark it explicitly as `Inference`.

### 4. Documentation Is Not Automatically Authoritative

README files, docs, comments, tests, and commit messages may provide clues, but they must not be treated as authoritative design truth by default.

Prefer scoped code evidence and user confirmation.

### 5. Snapshot Is Evidence, Not Conclusion

If a module-specific `snapshot.json` is available, use it as structural evidence only.

Do not infer design intent, code quality, or refactor needs solely from snapshot fields.

Large files, candidate entry points, directory names, and config files are reading signals, not design conclusions.

### 6. Conversation-First Is Supported

The user may explore the code through conversation first and defer document generation until they explicitly ask to summarize or update notes.

In conversation-first mode:

- Answer scoped code questions directly.
- Do not force file generation or file updates.
- Keep answers structured so they can be summarized later.
- Track useful observations in the conversation as facts, inferences, candidate takeaways, candidate lessons, open questions, and possible refactor topics.
- When the user asks to summarize, route stable conclusions into the correct repo-mentor documents.

### 7. Keep Onboarding Concise

`onboarding.md` should help a newcomer build a practical mental model quickly.

Move detailed design explanations, workflows, trade-offs, assumptions, takeaways, and lessons into `design-digest.md`.

### 8. Refactor Only When Triggered

Do not create or update `refactor-plan.md` from snapshot data alone.

Only create or update it when the user discusses:

- Refactoring.
- Technical debt.
- Maintainability issues.
- Design smells.
- Architecture evolution.
- Risky or confusing design that may become actionable.

---

## Skill Package Layout

This skill follows the Agent Skills folder model where the skill folder contains a required `SKILL.md` and may bundle scripts, references, assets, templates, and other resources.

Expected package layout:

```text
repo-mentor/
├── SKILL.md
├── scripts/
│   └── codebase_analyzer.py
├── references/
│   ├── analyzer-output-contract.md
│   ├── snapshot-consumption-contract.md
│   ├── document-routing-contract.md
│   └── workflows/
│       ├── scope-discovery.md
│       ├── scoped-snapshot-intake.md
│       ├── conversation-first-learning.md
│       ├── onboarding-initialization.md
│       ├── design-digest-distillation.md
│       └── refactor-planning.md
└── assets/
    └── templates/
        ├── scope-selection.template.md
        ├── onboarding.template.md
        ├── design-digest.template.md
        └── refactor-plan.template.md
```

---

## Target Repository Output Layout

When this skill is used on a repository, write repo-mentor outputs under the target repository root:

```text
.repo-mentor/
├── index.md                         # optional but recommended
├── scope-selection.md               # optional, repo-level, only when Scope Discovery is used
└── modules/
    └── <module-id>/
        ├── snapshot.json
        ├── onboarding.md
        ├── design-digest.md
        └── refactor-plan.md         # only when triggered
```

Rules:

- `.repo-mentor/` belongs at the repository root.
- Module-specific outputs must be placed under `.repo-mentor/modules/<module-id>/`.
- `scope-selection.md` is repo-level because it helps choose or refine module scope.
- `index.md` is repo-level and may list analyzed modules, note locations, status, and last-updated dates.
- Do not put module-specific outputs directly in `.repo-mentor/` unless there is only one temporary prototype session and the user explicitly requests it.

### Module ID Rule

Derive `<module-id>` from the normalized module scope path to avoid collisions.

Recommended normalization:

1. Trim leading and trailing slashes.
2. Replace `/`, `\`, whitespace, and `_` with `-`.
3. Convert to lowercase.
4. Remove characters that are unsuitable for file or directory names.
5. If the scope is `.`, use `repo-root`, but prefer Scope Discovery before analyzing repo root.

Examples:

```text
src/power_manager      -> src-power-manager
services/can_gateway   -> services-can-gateway
modules/DiagCore       -> modules-diagcore
app/common             -> app-common
lib/common             -> lib-common
```

---

## Default Workflow

Use the default workflow when the user already has a module scope.

### Step 1: Confirm Scope

Identify or confirm:

- Repository root.
- Module scope.
- Module ID.
- User goal.
- Whether the user wants document-first or conversation-first mode.
- Any known files, components, or workflows of interest.
- Whether a module-specific snapshot already exists.

If the scope is missing, too broad, or set to repository root, consider the optional Scope Discovery workflow.

### Step 2: Run Or Consume Scoped Snapshot

If appropriate, ask the user to run:

```bash
python scripts/codebase_analyzer.py /path/to/repo   --scope path/to/module   --max-depth 2   --ignore third_party   --ignore generated   --json   --output .repo-mentor/modules/<module-id>/snapshot.json
```

Use the generated snapshot as structural evidence.

For detailed snapshot rules, follow:

```text
references/analyzer-output-contract.md
references/snapshot-consumption-contract.md
references/workflows/scoped-snapshot-intake.md
```

### Step 3: Choose Interaction Mode

Support both modes:

#### Document-First Mode

Use when the user asks to immediately generate or update repo-mentor notes.

Proceed to initialize or update `onboarding.md` and `design-digest.md`.

#### Conversation-First Mode

Use when the user wants to ask code questions first and summarize later.

Follow:

```text
references/workflows/conversation-first-learning.md
```

In this mode, do not generate or update files until the user explicitly asks to summarize or persist notes.

### Step 4: Initialize Or Update Onboarding Notes

Create or update:

```text
.repo-mentor/modules/<module-id>/onboarding.md
```

Use:

```text
assets/templates/onboarding.template.md
references/workflows/onboarding-initialization.md
```

Keep this document beginner-friendly and concise.

### Step 5: Initialize Or Update Design Digest

Create or update:

```text
.repo-mentor/modules/<module-id>/design-digest.md
```

Use:

```text
assets/templates/design-digest.template.md
references/workflows/design-digest-distillation.md
```

This is the primary place for:

- Design intent.
- Key abstractions.
- Important workflows.
- Engineering trade-offs.
- Takeaways.
- Lessons learned.
- Hidden assumptions.
- Open questions.

### Step 6: Answer Technical Questions

When the user asks detailed technical questions:

1. Answer within the current module scope.
2. Separate evidence, inference, and uncertainty.
3. Capture candidate takeaways and lessons in the answer.
4. Keep onboarding-level information concise.
5. Put deeper technical details into `design-digest.md` only when the user wants notes updated.
6. Put uncertain items into `Open Questions` when summarizing or updating notes.

If the user is in conversation-first mode, defer file updates until the user asks to summarize or persist the discussion.

### Step 7: Summarize Conversation Into Notes When Asked

When the user asks to summarize, distill, persist, or update notes from the conversation:

- Put beginner-relevant stable knowledge in `.repo-mentor/modules/<module-id>/onboarding.md`.
- Put design intent, workflows, trade-offs, takeaways, lessons, and assumptions in `.repo-mentor/modules/<module-id>/design-digest.md`.
- Put uncertain or unresolved items in `Open Questions`.
- Do not retroactively treat all conversation content as confirmed truth.
- Classify content as facts, inferences, takeaways, lessons, and open questions.

### Step 8: Create Refactor Plan Only If Triggered

If the conversation includes refactoring, technical debt, maintainability issues, design smells, or architecture evolution, create or update:

```text
.repo-mentor/modules/<module-id>/refactor-plan.md
```

Use:

```text
assets/templates/refactor-plan.template.md
references/workflows/refactor-planning.md
```

A refactor plan must include:

- Trigger.
- Scope.
- Observed pain points.
- What should be preserved.
- Goals.
- Non-goals.
- Proposed safe steps.
- Risk assessment.
- Validation strategy.
- Rollback strategy.

---

## Optional Workflow: Scope Discovery

Use Scope Discovery only when:

- The user has not provided a module scope.
- The selected scope is the repository root.
- The selected scope appears too large.
- The repository has unclear or weak module boundaries.
- The conversation repeatedly crosses the current scope.
- The user explicitly asks for help choosing a module scope.

Scope Discovery may use a shallow repository-level snapshot, but only to recommend or refine a manageable module scope.

It must not produce:

- Whole-repository design conclusions.
- Whole-repository architecture judgments.
- Global technical debt lists.
- Global refactor plans.

If Scope Discovery is used, create or update:

```text
.repo-mentor/scope-selection.md
```

Use:

```text
assets/templates/scope-selection.template.md
references/workflows/scope-discovery.md
```

If a repo-level snapshot is needed during Scope Discovery, write it as:

```text
.repo-mentor/repo-snapshot.json
```

Do not use `repo-snapshot.json` as input for module-level onboarding or design conclusions. Use it only for scope selection.

---

## Optional Repository Index

When multiple modules are analyzed, create or update:

```text
.repo-mentor/index.md
```

The index may include:

```markdown
# Repo Mentor Index

## Modules

- `src/power_manager`
  - Module ID: `src-power-manager`
  - Notes: `.repo-mentor/modules/src-power-manager/`
  - Status: active
  - Last updated: YYYY-MM-DD
```

Do not turn `index.md` into a whole-repository design summary.

---

## Output Documents

### Always Maintain When Activated For A Scoped Module And Summary Is Requested

```text
.repo-mentor/modules/<module-id>/onboarding.md
.repo-mentor/modules/<module-id>/design-digest.md
```

In conversation-first mode, these may be deferred until the user asks to summarize or update notes.

### Generated By Analyzer For A Scoped Module

```text
.repo-mentor/modules/<module-id>/snapshot.json
```

### Conditional Module Output

```text
.repo-mentor/modules/<module-id>/refactor-plan.md
```

Create only when refactor-related discussion exists.

### Optional Repo-Level Outputs

```text
.repo-mentor/scope-selection.md
.repo-mentor/repo-snapshot.json
.repo-mentor/index.md
```

Create only when needed.

---

## Document Routing Rules

Use these routing rules when deciding where information belongs.

### Put In `onboarding.md`

Use for:

- Module scope.
- Short module responsibility summary.
- Practical mental model.
- Key concepts for newcomers.
- Suggested reading path.
- Top-level structure.
- Common newcomer pitfalls.
- Links to deeper design notes.

Do not put deep implementation details here.

### Put In `design-digest.md`

Use for:

- Design intent.
- Inferred intent.
- Key abstractions.
- Important workflows.
- Engineering trade-offs.
- Takeaways.
- Lessons learned.
- Hidden assumptions.
- Evidence.
- Open questions.

This is the core knowledge-distillation document.

### Put In `refactor-plan.md`

Use for:

- Refactor triggers.
- Pain points.
- Design smells.
- What should be preserved.
- Refactor goals and non-goals.
- Step-by-step safe plan.
- Risks.
- Validation.
- Rollback.

Only update this document when the user raises refactor-related topics.

### Put In `scope-selection.md`

Use for:

- Candidate module scopes.
- Recommended initial scope.
- Scope risks.
- Boundary rules.
- Excluded areas.
- Scope-related open questions.

Only update this document during Scope Discovery.

---

## Evidence And Inference Style

When answering or updating documents, use explicit labels.

Example:

```markdown
Fact:
- `FooController` calls `BarDispatcher` during initialization.

Inference:
- The module likely separates orchestration from dispatching to keep workflow control independent from transport details.

Evidence:
- `src/foo/FooController.cpp`
- `src/foo/BarDispatcher.h`

Open Question:
- It is not yet clear whether this separation is intentional or historical.
```

Avoid presenting inferred design intent as confirmed fact.

---

## Refactor Safety Rules

When producing refactor advice:

- Preserve good existing design choices.
- Prefer small, reversible steps.
- Avoid large rewrites.
- Avoid cross-scope changes unless the user explicitly expands scope.
- Include validation strategy.
- Include rollback strategy.
- Separate lessons learned from actionable refactor steps.
- Do not recommend refactoring solely because a file is large.

---

## Bundled Resources

### Scripts

```text
scripts/codebase_analyzer.py
```

Used to generate compact structural snapshots for scoped modules.

### References

```text
references/analyzer-output-contract.md
references/snapshot-consumption-contract.md
references/document-routing-contract.md
references/workflows/scope-discovery.md
references/workflows/scoped-snapshot-intake.md
references/workflows/conversation-first-learning.md
references/workflows/onboarding-initialization.md
references/workflows/design-digest-distillation.md
references/workflows/refactor-planning.md
```

### Templates

```text
assets/templates/scope-selection.template.md
assets/templates/onboarding.template.md
assets/templates/design-digest.template.md
assets/templates/refactor-plan.template.md
```

---

## Do Not

Do not:

- Analyze the whole repository by default.
- Treat README/docs/tests/comments as authoritative design truth by default.
- Generate repo-wide architecture conclusions during Scope Discovery.
- Create refactor plans from snapshot data alone.
- Judge code quality without evidence.
- Hide uncertainty.
- Overload `onboarding.md` with deep technical details.
- Expand beyond the selected module scope without user confirmation.
- Mix outputs from different modules in the same document directory.
- Store module-specific outputs directly under `.repo-mentor/` when `.repo-mentor/modules/<module-id>/` should be used.
- Force document generation in conversation-first mode before the user asks to summarize or update notes.
