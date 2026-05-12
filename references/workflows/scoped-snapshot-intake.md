# Workflow: Scoped Snapshot Intake

## Purpose

Generate or consume a compact structural snapshot for a selected module scope.

The snapshot provides evidence for onboarding and design learning, not conclusions.

---

## Inputs

- repository root
- module scope
- module ID
- optional ignore patterns
- optional existing snapshot

---

## Command

```bash
python scripts/codebase_analyzer.py /path/to/repo   --scope path/to/module   --max-depth 2   --ignore third_party   --ignore generated   --json   --output .repo-mentor/modules/<module-id>/snapshot.json
```

---

## Steps

1. Confirm `repo_root` and `scope`.
2. Derive `<module-id>` from the normalized scope path.
3. Run or request the analyzer command.
4. Verify `snapshot.json` contains `schema_version`, `scope`, `scan_policy`, `summary`, and `warnings`.
5. Check for scope warnings.
6. If scope is too broad, suggest Scope Discovery.
7. Use snapshot only as structural evidence.

---

## Expected Output

```text
.repo-mentor/modules/<module-id>/snapshot.json
```

---

## Consumption Rules

Follow:

```text
references/analyzer-output-contract.md
references/snapshot-consumption-contract.md
```

Do not use snapshot fields as design conclusions.
