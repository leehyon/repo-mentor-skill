# Workflow: Scope Discovery

## Purpose

Scope Discovery helps choose or refine a manageable module scope for `repo-mentor`.

It is optional and must not become whole-repository design analysis.

---

## When To Use

Use this workflow when:

- the user has not provided a module scope
- the selected scope is the repository root
- the selected scope appears too large
- the repository has unclear or weak module boundaries
- the conversation repeatedly crosses the current scope
- the user explicitly asks for help choosing a module scope

---

## Inputs

- repository root
- user goal
- optional known area of interest
- optional ignore patterns
- optional shallow repo-level snapshot

---

## Optional Command

```bash
python scripts/codebase_analyzer.py /path/to/repo   --scope .   --max-depth 2   --ignore third_party   --ignore generated   --json   --output .repo-mentor/repo-snapshot.json
```

Use this repository-level snapshot only for scope selection.

---

## Output

Create or update:

```text
.repo-mentor/scope-selection.md
```

Use:

```text
assets/templates/scope-selection.template.md
```

---

## Steps

1. Identify why Scope Discovery is needed.
2. Review repository-level structural signals only.
3. Identify candidate module scopes.
4. Evaluate candidates against the user's goal.
5. Mark risks and unknowns for each candidate.
6. Recommend one initial scope.
7. Define boundary rules for the session.
8. Record excluded areas.
9. Put unresolved issues in `Open Questions`.

---

## Non-Goals

Do not produce:

- whole-repository architecture summary
- global technical debt list
- global refactor plan
- repository-wide design intent
- code quality ranking

---

## Completion Criteria

This workflow is complete when there is a recommended or confirmed module scope and a clear module ID for module-specific outputs.
