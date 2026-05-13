# Analyzer Output Contract

`codebase_analyzer.py` generates an objective structural snapshot for a scoped module. It collects reproducible facts only and must not infer design intent, judge code quality, summarize documentation, or produce refactor recommendations.

Required top-level fields:

```json
{
  "schema_version": "1.0",
  "tool": {},
  "scope": {},
  "scan_policy": {},
  "summary": {},
  "languages": {},
  "top_extensions": {},
  "key_config_files": [],
  "candidate_entry_points": [],
  "largest_files_by_size": [],
  "largest_files_by_lines": [],
  "suspected_generated_or_vendored": [],
  "directory_structure": [],
  "warnings": []
}
```

`docs_are_authoritative` and `semantic_document_analysis` should be `false` by default.

Use `.repo-mentor/modules/<module-id>/snapshot.json` for module snapshots. Use `.repo-mentor/repo-snapshot.json` only for Scope Discovery.
