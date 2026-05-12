# Analyzer Output Contract

## Purpose

`codebase_analyzer.py` generates an objective, compact structural snapshot for a scoped module in a repository.

It collects reproducible facts only. It must not infer design intent, judge code quality, summarize documentation, or produce refactor recommendations.

---

## Scope Model

The analyzer must distinguish between:

- `repo_root`: the repository root.
- `scope`: the user-selected module path relative to `repo_root`.
- `scope_root`: the resolved absolute path for the selected scope.
- `scope_policy`: expected to be `module-only`.

By default, statistics are computed only inside `scope_root`.

If `scope` is `.` or resolves to `repo_root`, the analyzer should emit a warning so `repo-mentor` can consider Scope Discovery.

---

## Structural Facts Only

The analyzer may output:

- file counts
- directory counts
- recognized source file counts
- language distribution based on file extension
- top file extensions
- key config files
- candidate entry points
- largest files by size
- largest files by lines
- suspected generated or vendored files
- compact directory structure
- warnings
- scan policy

The analyzer must not output:

- design intent
- architecture summary
- README summary
- docs summary
- tests summary
- code quality scores
- refactor suggestions
- global technical debt lists
- whole-repository design conclusions

---

## Documentation Authority

The analyzer must not treat README files, docs, tests, comments, or commit messages as authoritative design truth.

It should explicitly set:

```json
{
  "docs_are_authoritative": false,
  "semantic_document_analysis": false
}
```

These fields tell `repo-mentor` that the snapshot contains structural evidence only.

---

## Required JSON Top-Level Fields

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

---

## Field Definitions

### `schema_version`

Schema version for compatibility.

Example:

```json
"schema_version": "1.0"
```

### `tool`

Identifies the tool and generation time.

```json
{
  "name": "codebase_analyzer.py",
  "purpose": "scoped structural snapshot",
  "generated_at": "2026-05-12T09:00:00+00:00"
}
```

### `scope`

Defines the analysis boundary.

```json
{
  "repo_root": "/path/to/repo",
  "scope": "src/foo",
  "scope_root": "/path/to/repo/src/foo",
  "scope_policy": "module-only"
}
```

### `scan_policy`

Records how the scan was performed.

```json
{
  "max_depth": 2,
  "default_ignored_dirs": [".git", "node_modules", "build"],
  "extra_ignored_patterns": ["third_party", "generated"],
  "docs_are_authoritative": false,
  "semantic_document_analysis": false
}
```

### `summary`

Compact scale information.

```json
{
  "file_count": 128,
  "directory_count": 24,
  "recognized_source_file_count": 92
}
```

### `languages`

Extension-based language detection. Treat as approximate.

```json
{
  "C++": 42,
  "C": 18,
  "Python": 6
}
```

### `top_extensions`

Top file extensions by count.

```json
{
  ".cpp": 30,
  ".h": 24,
  ".json": 6
}
```

### `key_config_files`

Config anchors found in scope or repo root.

```json
[
  {
    "path": "CMakeLists.txt",
    "location": "scope"
  }
]
```

### `candidate_entry_points`

Heuristic reading anchors only. They are not confirmed runtime entry points.

```json
[
  {
    "path": "src/foo/main.cpp",
    "reason": "filename matches main.* pattern"
  }
]
```

### `largest_files_by_size`

Largest files by bytes.

```json
[
  {
    "path": "src/foo/table.cpp",
    "bytes": 183244,
    "size": "178.9KB"
  }
]
```

### `largest_files_by_lines`

Largest text/source files by line count.

```json
[
  {
    "path": "src/foo/state_machine.cpp",
    "lines": 2410
  }
]
```

### `suspected_generated_or_vendored`

Files or paths that should be down-weighted during design inference.

```json
[
  {
    "path": "src/foo/generated/messages.pb.cc",
    "reason": "filename suggests generated protobuf output"
  }
]
```

### `directory_structure`

Compact structure listing, bounded by `max_depth` and output limits.

```json
[
  "src/foo/",
  " state/",
  "  state_machine.cpp"
]
```

### `warnings`

Non-fatal scan warnings.

```json
[
  {
    "code": "SCOPE_IS_REPO_ROOT",
    "message": "No explicit scope was provided; analysis covers the entire repository."
  }
]
```

---

## Output Location

For scoped module analysis, write snapshots to:

```text
.repo-mentor/modules/<module-id>/snapshot.json
```

For optional Scope Discovery, a shallow repository-level snapshot may be written to:

```text
.repo-mentor/repo-snapshot.json
```

`repo-snapshot.json` must be used only for scope selection, not for module-level design conclusions.
