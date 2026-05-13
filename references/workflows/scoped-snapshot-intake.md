# Workflow: Scoped Snapshot Intake

Generate or consume a compact structural snapshot for the selected module.

```bash
python scripts/codebase_analyzer.py /path/to/repo \
  --scope path/to/module \
  --max-depth 2 \
  --ignore third_party \
  --ignore generated \
  --json \
  --output .repo-mentor/modules/<module-id>/snapshot.json
```

Use the snapshot as structural evidence only.
