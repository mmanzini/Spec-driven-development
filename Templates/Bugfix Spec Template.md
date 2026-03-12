---
type: template
sdd-version: "0.1"
artifact: bugfix-spec
---

# Bugfix Spec Template

> [!info] Create a folder at `specs/[bugfix-name]/` and split this into two files: `bugfix.md` and `tasks.md`. Use this for bugs where regressions are costly or the fix requires investigation.

---

## bugfix.md

# [Bug Name] — Bugfix Analysis

## Bug Summary

[One paragraph: what's broken, who is affected, and how severe is it?]

## Current Behavior (Defective)

[What happens now. Be precise — include steps to reproduce.]

1. [Step 1]
2. [Step 2]
3. [Observed result — what goes wrong]

## Expected Behavior (Correct)

[What should happen instead. Be specific enough that this becomes a test case.]

1. [Step 1]
2. [Step 2]
3. [Expected result]

## Unchanged Behavior (Regression Prevention)

[What existing functionality must NOT be affected by the fix. These become regression test cases.]

- [Behavior 1 that must continue working]
- [Behavior 2 that must continue working]

> [!tip] This section is critical. It prevents the fix from breaking something else. Think about what users currently do that works fine and must keep working.

## Root Cause Analysis

[What is causing the defect? If unknown, describe your investigation approach.]

> [!tip] This section may be filled in during investigation. It's okay to start with a hypothesis and update it.

## Proposed Fix

[High-level description of the fix approach. Not the code — the strategy.]

## Boundaries

### Always
- [e.g., "Preserve existing API contract"]

### Never
- [e.g., "Never modify the user table schema"]

---

## tasks.md

# [Bug Name] — Fix Tasks

### 1. Reproduce the bug

- [ ] **Status:** Not started
- **Description:** Create a reliable reproduction of the defective behavior
- **Validates:** Current Behavior section

### 2. Implement the fix

- [ ] **Status:** Not started
- **Description:** [Specific fix based on root cause analysis]
- **Files:** [Which files to modify]
- **Validates:** Expected Behavior section

### 3. Verify regression prevention

- [ ] **Status:** Not started
- **Description:** Confirm all unchanged behaviors still work
- **Validates:** Unchanged Behavior section

### 4. [Additional tasks as needed]

- [ ] **Status:** Not started
- **Description:** [What to do]
- **Depends on:** [Previous task]

---

> [!tip] Delete all `> [!tip]` callouts when done. For simple bugs, tasks 1-3 may be all you need.
