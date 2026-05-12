# Refactor Plan

## Trigger

What triggered this refactor discussion?

Examples:

- User asked whether a component should be refactored.
- A maintainability issue was discussed.
- A design smell was identified through code evidence.
- A lesson learned became actionable.
- The user asked for architecture evolution options.

Current trigger:

```text
<TODO: describe the conversation or evidence that triggered this plan>
```

---

## Scope

- Module scope: `<TODO: scope>`
- Scope policy: `module-only`

### In Scope

- `<TODO: files/directories/components included in the refactor discussion>`
- `<TODO>`

### Out of Scope

- `<TODO: files/directories/components intentionally excluded>`
- `<TODO>`

---

## Observed Pain Points

Each pain point should include evidence and impact.

### Pain Point: `<TODO: short name>`

- Description: `<TODO>`
- Evidence: `<TODO: file/path/conversation evidence>`
- Impact: `<TODO>`
- Confidence: `<TODO: Low / Medium / High>`

### Pain Point: `<TODO: short name>`

- Description: `<TODO>`
- Evidence: `<TODO>`
- Impact: `<TODO>`
- Confidence: `<TODO: Low / Medium / High>`

---

## Design Smells

Only include smells supported by evidence.

Examples:

- unclear boundary
- mixed responsibilities
- implicit lifecycle dependency
- duplicated decision logic
- inconsistent error handling
- overly broad abstraction
- insufficient test seam

Current design smells:

### Design Smell: `<TODO: short name>`

- Description: `<TODO>`
- Evidence: `<TODO>`
- Why it matters: `<TODO>`
- Confidence: `<TODO: Low / Medium / High>`

---

## What Should Be Preserved

This section is mandatory.

Capture good existing design ideas that must survive the refactor.

Examples:

- stable interface
- useful abstraction
- proven fallback behavior
- testable seam
- performance-critical path
- hardware/platform constraint
- compatibility behavior

Current preservation targets:

- `<TODO: design element to preserve>`
  - Why it should be preserved: `<TODO>`
  - Evidence: `<TODO>`

- `<TODO: design element to preserve>`
  - Why it should be preserved: `<TODO>`
  - Evidence: `<TODO>`

---

## Refactor Goals

What the refactor should improve.

- `<TODO: goal>`
- `<TODO: goal>`
- `<TODO: goal>`

---

## Non-goals

What the refactor should not try to solve.

This prevents scope creep.

- `<TODO: non-goal>`
- `<TODO: non-goal>`
- `<TODO: non-goal>`

---

## Proposed Steps

Use small, safe steps. Prefer behavior-preserving changes before structural changes.

1. `<TODO: add characterization tests or behavior snapshots>`
   - Expected outcome: `<TODO>`
   - Risk: `<TODO>`

2. `<TODO: extract or isolate a small piece without behavior change>`
   - Expected outcome: `<TODO>`
   - Risk: `<TODO>`

3. `<TODO: introduce or clarify an interface boundary>`
   - Expected outcome: `<TODO>`
   - Risk: `<TODO>`

4. `<TODO: migrate one call site or workflow>`
   - Expected outcome: `<TODO>`
   - Risk: `<TODO>`

5. `<TODO: validate behavior and repeat>`
   - Expected outcome: `<TODO>`
   - Risk: `<TODO>`

---

## Risk Assessment

### Risk: `<TODO: risk name>`

- Why it matters: `<TODO>`
- Likelihood: `<TODO: Low / Medium / High>`
- Impact: `<TODO: Low / Medium / High>`
- Mitigation: `<TODO>`

### Risk: `<TODO: risk name>`

- Why it matters: `<TODO>`
- Likelihood: `<TODO: Low / Medium / High>`
- Impact: `<TODO: Low / Medium / High>`
- Mitigation: `<TODO>`

---

## Validation Strategy

How to prove behavior is preserved.

Possible validation methods:

- unit tests
- integration tests
- golden output
- logs
- runtime metrics
- simulation
- hardware-in-loop validation
- manual smoke tests
- static analysis

Current validation plan:

- `<TODO: validation method>`
  - What it proves: `<TODO>`
  - Required before step: `<TODO>`

- `<TODO: validation method>`
  - What it proves: `<TODO>`
  - Required before step: `<TODO>`

---

## Rollback Strategy

How to safely revert if the refactor causes issues.

- Rollback trigger: `<TODO>`
- Rollback method: `<TODO>`
- Files/components affected: `<TODO>`
- Data/config compatibility considerations: `<TODO>`

---

## Migration Notes

Use this section if the refactor requires staged migration.

- Compatibility constraints: `<TODO>`
- Temporary adapters/shims: `<TODO>`
- Deprecation plan: `<TODO>`
- Cleanup criteria: `<TODO>`

---

## Open Questions

Questions blocking or shaping the refactor.

- `<TODO: question>`
- `<TODO: question>`
- `<TODO: question>`

---

## Decision Status

```text
<TODO: Proposed / Confirmed / Paused / Rejected / Completed>
```

Decision notes:

```text
<TODO: current decision summary>
```

---

## Update Log

- `<YYYY-MM-DD>`: Created initial refactor plan.
- `<YYYY-MM-DD>`: `<TODO: update summary>`
