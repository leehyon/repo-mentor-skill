# repo-mentor

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

---

## What This Skill Produces

When used on a target repository, `repo-mentor` writes its outputs under the repository root:

```text
.repo-mentor/
├── index.md                         # optional but recommended when multiple modules are analyzed
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

### Document Roles

#### `snapshot.json`

A machine-generated structural snapshot of the selected module.

It contains objective facts such as file counts, detected languages, config anchors, candidate entry points, large files, suspected generated/vendor files, and compact directory structure.

It is evidence, not a design conclusion.

#### `onboarding.md`

A concise guide for newcomers.

Use it for:

- module scope;
- short responsibility summary;
- practical mental model;
- key concepts;
- suggested reading path;
- common newcomer pitfalls;
- links to deeper notes.

Do not put deep implementation details here.

#### `design-digest.md`

A module-specific design deep dive.

Use it for:

- current understanding;
- design intent;
- inferred design intent;
- key abstractions;
- important workflows;
- engineering trade-offs;
- hidden assumptions;
- module-specific observations;
- evidence and open questions.

Reusable lessons should be marked as candidates here and distilled into `engineering-lessons.md`.

#### `engineering-lessons.md`

Reusable engineering knowledge distilled from the module.

Use it for:

- reusable design takeaways;
- lessons learned;
- design heuristics;
- anti-patterns to avoid;
- applicability conditions;
- when to reuse or avoid an idea;
- links back to evidence in `design-digest.md` and code.

Avoid presenting module-derived lessons as universal best practices without applicability conditions.

#### `refactor-plan.md`

A safe, scoped refactor plan.

Create or update it only when the user explicitly discusses:

- refactoring;
- technical debt;
- maintainability issues;
- design smells;
- architecture evolution.

Do not create it from snapshot data alone.

#### `scope-selection.md`

A repo-level helper document used only during Scope Discovery.

Use it when the module boundary is unclear or the user does not know which scope to choose.

It is not a whole-repository architecture analysis.

---

## Skill Package Layout

The skill package should look like this:

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
│       ├── engineering-lessons-distillation.md
│       └── refactor-planning.md
└── assets/
    └── templates/
        ├── scope-selection.template.md
        ├── onboarding.template.md
        ├── design-digest.template.md
        ├── engineering-lessons.template.md
        └── refactor-plan.template.md
```

---

## Installing In OpenCode

OpenCode discovers skills from project-local and global skill directories.

### Global Installation

Use this if you want `repo-mentor` available in all repositories:

```text
~/.config/opencode/skills/repo-mentor/
```

Example:

```bash
mkdir -p ~/.config/opencode/skills
cp -R repo-mentor ~/.config/opencode/skills/repo-mentor
```

### Project-Local Installation

Use this if you want `repo-mentor` available only in one repository:

```text
<your-repo>/.opencode/skills/repo-mentor/
```

Example:

```bash
mkdir -p .opencode/skills
cp -R /path/to/repo-mentor .opencode/skills/repo-mentor
```

### Important Naming Rule

The folder name should match the skill name in `SKILL.md`:

```text
repo-mentor
```

---

## Basic Usage In OpenCode

Open the target repository in OpenCode, then start your prompt with:

```text
Use the repo-mentor skill.
```

or:

```text
Load and follow the repo-mentor skill instructions.
```

This makes the intended skill explicit.

---

## Recommended Interaction Modes

`repo-mentor` supports two primary modes.

## 1. Document-First Mode

Use this when you want `repo-mentor` to generate or update notes immediately.

Example prompt:

```text
Use the repo-mentor skill.

Module scope:
`src/power_manager`

Module ID:
`src-power-manager`

Goal:
Help me understand and learn the current design of this module.

Please:
1. Keep the analysis scoped to `src/power_manager`.
2. Check whether `.repo-mentor/modules/src-power-manager/snapshot.json` exists.
3. If missing, provide the analyzer command.
4. Initialize or update:
   - `.repo-mentor/modules/src-power-manager/onboarding.md`
   - `.repo-mentor/modules/src-power-manager/design-digest.md`
   - `.repo-mentor/modules/src-power-manager/engineering-lessons.md` if reusable lessons exist
5. Do not create `refactor-plan.md` unless I explicitly discuss refactoring.
```

## 2. Conversation-First Mode

Use this when you want to ask code questions first and summarize later.

Example prompt:

```text
Use the repo-mentor skill.

I want to use conversation-first mode for module `src/power_manager`.

For now:
- Do not generate or update files.
- Keep the discussion scoped to this module.
- Answer my code questions.
- Separate facts, inference, and open questions.
- Track possible module-specific observations for design-digest.md.
- Track reusable engineering lessons for engineering-lessons.md.

I will ask you later to summarize into repo-mentor notes.
```

Then ask normal code questions, for example:

```text
Why does this module initialize the state machine before registering callbacks?
```

```text
Explain the relationship between PowerManager, StateController, and EventDispatcher.
```

```text
What assumptions does this module make about lifecycle order and ownership?
```

Later, when you are ready to persist the discussion:

```text
Now summarize our discussion into repo-mentor notes.

Please update:
- `.repo-mentor/modules/src-power-manager/onboarding.md`
- `.repo-mentor/modules/src-power-manager/design-digest.md`
- `.repo-mentor/modules/src-power-manager/engineering-lessons.md`

Only create `refactor-plan.md` if our conversation included actionable refactor discussion.
```

---

## Running The Analyzer

The analyzer creates a compact structural snapshot for a selected module.

If the skill is installed globally:

```bash
python ~/.config/opencode/skills/repo-mentor/scripts/codebase_analyzer.py .   --scope src/power_manager   --max-depth 2   --ignore third_party   --ignore generated   --json   --output .repo-mentor/modules/src-power-manager/snapshot.json
```

If the skill is installed in the project:

```bash
python .opencode/skills/repo-mentor/scripts/codebase_analyzer.py .   --scope src/power_manager   --max-depth 2   --ignore third_party   --ignore generated   --json   --output .repo-mentor/modules/src-power-manager/snapshot.json
```

The snapshot should be treated as structural evidence only.

Do not infer design intent, code quality, or refactor needs from snapshot fields alone.

---

## Module ID Convention

Module outputs are grouped under:

```text
.repo-mentor/modules/<module-id>/
```

Recommended module ID normalization:

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

## When Module Boundaries Are Unclear

If you do not know which module to analyze, use Scope Discovery.

Example prompt:

```text
Use the repo-mentor skill.

I am not sure what module scope to choose in this repository.
Please run Scope Discovery.

Constraints:
- Do not analyze the whole repository design.
- Do not create a global refactor plan.
- Only recommend a manageable initial module scope.
- Create or update `.repo-mentor/scope-selection.md` if needed.
```

Scope Discovery may use a shallow repo-level snapshot:

```bash
python ~/.config/opencode/skills/repo-mentor/scripts/codebase_analyzer.py .   --scope .   --max-depth 2   --ignore third_party   --ignore generated   --json   --output .repo-mentor/repo-snapshot.json
```

Use `repo-snapshot.json` only for scope selection, not for repo-wide design conclusions.

---

## Common Prompt Recipes

### Start Learning A Known Module

```text
Use the repo-mentor skill.

Help me learn the design of `src/power_manager`.
Keep the scope limited to this module.
Create or update notes under `.repo-mentor/modules/src-power-manager/`.
Do not create a refactor plan unless I explicitly ask for refactoring.
```

### Ask A Design Question

```text
Use the repo-mentor skill.

Within module scope `src/power_manager`, explain why the event dispatch logic is separated from state transition logic.

Please:
- separate facts from inference
- cite code evidence by file path
- identify module-specific observations for design-digest.md
- identify reusable lessons for engineering-lessons.md
- do not expand beyond the current module scope
```

### Extract Reusable Engineering Lessons

```text
Use the repo-mentor skill.

From our discussion about `src/power_manager`, extract reusable engineering lessons.

Please update:
`.repo-mentor/modules/src-power-manager/engineering-lessons.md`

For each lesson, include:
- source context
- why it matters
- reusable guidance
- when to use it
- when not to use it
- evidence or links back to design-digest.md
```

### Update Notes After A Conversation

```text
Use the repo-mentor skill.

Summarize our conversation into repo-mentor notes for `src/power_manager`.

Update:
- onboarding.md for beginner-relevant stable knowledge
- design-digest.md for module-specific design details
- engineering-lessons.md for reusable engineering lessons

Only update refactor-plan.md if our conversation included actionable refactor topics.
```

### Ask For Refactor Planning

```text
Use the repo-mentor skill.

I think the state machine code in `src/power_manager` may need refactoring.

Please:
- evaluate the maintainability concern within the current scope
- identify what should be preserved
- propose a safe incremental refactor plan
- include validation and rollback strategy
- create or update `.repo-mentor/modules/src-power-manager/refactor-plan.md`
```

---

## Interaction Guidelines

When using `repo-mentor`, try to provide:

- the module scope;
- the module ID, if known;
- the files or symbols you are asking about;
- whether you want document-first or conversation-first mode;
- whether notes should be updated now or later;
- whether refactoring is actually in scope.

Good prompt shape:

```text
Use the repo-mentor skill.

Mode: conversation-first
Module scope: `<path/to/module>`
Module ID: `<module-id>`
Question: `<your question>`

Please stay within scope, separate facts from inference, and track reusable lessons for later summarization.
```

---

## Important Rules

`repo-mentor` should:

- stay module-scoped by default;
- treat snapshots as evidence, not conclusions;
- avoid treating README/docs/tests/comments as authoritative design truth by default;
- distinguish facts, inference, and open questions;
- keep onboarding concise;
- keep module-specific details in `design-digest.md`;
- keep reusable lessons in `engineering-lessons.md`;
- create `refactor-plan.md` only when refactoring is explicitly discussed;
- avoid presenting module-derived lessons as universal best practices without applicability conditions.

---

## Typical End-To-End Flow

```text
1. Choose or discover module scope.
2. Generate module snapshot.
3. Ask code and design questions.
4. Build or update onboarding.md.
5. Build or update design-digest.md.
6. Distill reusable lessons into engineering-lessons.md.
7. Create refactor-plan.md only if refactoring is discussed.
```

---

## Status

This skill is intended to be used iteratively.

The notes it creates are living documents. They should be updated as the engineer asks more questions, confirms or corrects design understanding, discovers hidden assumptions, and extracts reusable engineering lessons.
