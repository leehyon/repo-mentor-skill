# Workflow: Scope Discovery

Use when the user has no clear scope, selected repo root, chose an overly large scope, or reports unclear module boundaries.

Purpose: recommend or refine a manageable module scope. Do not analyze whole-repository architecture.

Optional command:

```bash
python scripts/codebase_analyzer.py /path/to/repo \
  --scope . \
  --max-depth 2 \
  --ignore third_party \
  --ignore generated \
  --json \
  --output .repo-mentor/repo-snapshot.json
```

Output: `.repo-mentor/scope-selection.md`.
