# Test Plan Purpose

The Test Plan captures the explicit output of Step 1 of the TDD loop before any RED-GREEN-REFACTOR cycle starts. It documents the reasoning used to select tests (factors, equivalence classes, boundaries, and combinatorial reductions), the agreed test list, and the execution approval policy.

## Instructions for the Agent

### 1. Input Baseline

- Build the plan from the active use-case context and the selected scenario slice.
- If available, align with `Use Case Realization` and `Iteration Plan` artifacts.
- Keep traceability from test cases to requirements/scenario steps.

### 2. Test Design Rationale

- Identify relevant factors for the scenario.
- Define valid and invalid equivalence classes.
- Define boundary values and include just-below/at/just-above cases when applicable.
- Apply combinatorial reduction (pairwise/orthogonal/explicit set) when combinations are large.
- Explain why each selected case is included and why excluded combinations are acceptable.

### 3. Agreed Test List (Step 1 Output)

- Persist the agreed test list as the formal output of Step 1.
- Each test item must include preconditions, trigger/input, and expected result.
- Include priority and rationale for each selected test item.

### 4. Approval and Execution Policy

- Record the chosen implementation mode:
  - `Guided mode`: per-case approval before RED.
  - `Automatic mode`: sequential execution of the agreed list (one case at a time, full `RED -> GREEN -> REFACTOR` per case) without per-case approval.
- Record approval evidence (message, token, or equivalent confirmation).

### 5. Quality and Scope Rules

- Keep the plan focused on behavior and verification intent, not on implementation details.
- Exclude infrastructure and algorithm details that do not affect test intent.
- If information is missing, keep sections and mark them as `TBD`.

## Storage Convention

- Persist the test plan artifact under:
  - `05 Test/Test plan.md`

## Validation Checklist

1. Is the test scope clearly bounded (in/out of scope)?
2. Are factors, equivalence classes, and boundary values explicit?
3. Is combinatorial strategy stated and justified?
4. Does the agreed test list include rationale and expected results?
5. Is approval/execution mode documented with evidence?
6. Is traceability to scenario/use-case steps explicit?
7. Is the storage path and file name compliant?
