# Snapshot Consumption Contract

## Purpose

This contract defines how `repo-mentor` consumes `snapshot.json`.

A snapshot is structural evidence. It is not a design conclusion.

---

## Core Rule

`repo-mentor` must treat snapshot fields as reading signals and evidence only.

Do not infer the following solely from snapshot data:

- design intent
- architecture style
- code quality
- technical debt
- refactor necessity
- module ownership
- runtime behavior

---

## Scope Enforcement

Read the current module scope from:

```json
{
  "scope": {
    "repo_root": "...",
    "scope": "...",
    "scope_root": "...",
    "scope_policy": "module-only"
  }
}
```

All analysis should remain inside `scope_root` unless the user explicitly updates the scope.

If the user asks about an external module, answer only at boundary level unless scope is updated.

---

## Field-To-Document Mapping

### `onboarding.md`

Snapshot fields that may help initialize or update onboarding:

- `scope`
- `summary`
- `languages`
- `top_extensions`
- `key_config_files`
- `candidate_entry_points`
- `directory_structure`
- `warnings`

Use these fields to help a newcomer orient themselves. Do not turn them into deep design conclusions.

### `design-digest.md`

Snapshot fields that may be used as evidence:

- `scope`
- `directory_structure`
- `key_config_files`
- `candidate_entry_points`
- `largest_files_by_lines`
- `largest_files_by_size`
- `suspected_generated_or_vendored`
- `languages`
- `top_extensions`
- `warnings`

Place these under an evidence section such as `Evidence From Snapshot`.

### `refactor-plan.md`

Do not create or update `refactor-plan.md` from snapshot alone.

Snapshot facts may support a refactor discussion only after the user raises refactoring, technical debt, maintainability, design smell, or architecture evolution.

### `scope-selection.md`

A repository-level snapshot may be used only for Scope Discovery.

Do not use repo-level snapshot data for whole-repository design analysis.

---

## Safe Interpretations

Acceptable wording:

```text
The snapshot shows several large files worth inspecting.
```

```text
The directory structure suggests possible reading anchors, but this needs code-level confirmation.
```

```text
This file is marked as suspected generated output and should be down-weighted for design inference.
```

Avoid wording like:

```text
This large file is a god object.
```

```text
This repository uses layered architecture.
```

```text
This module needs refactoring because the file count is high.
```

---

## Documentation Handling

If the snapshot says:

```json
"docs_are_authoritative": false,
"semantic_document_analysis": false
```

then `repo-mentor` must not assume README/docs/tests/comments were analyzed as design truth.

If user-provided documentation is later used, label it as a claim or clue unless confirmed by scoped code evidence.

---

## Warning Handling

If warnings include `SCOPE_IS_REPO_ROOT`, `SCOPE_RESOLVES_TO_REPO_ROOT`, or `LARGE_SCOPE`, suggest Scope Discovery or ask the user to narrow scope.

If warnings include many generated or vendored files, down-weight those areas and consider extra ignore patterns.

---

## Output Location Awareness

For module-specific work, consume:

```text
.repo-mentor/modules/<module-id>/snapshot.json
```

For Scope Discovery only, consume:

```text
.repo-mentor/repo-snapshot.json
```
