---
type: template
sdd-version: "0.1"
artifact: task-list
---

# Task List Template

> [!info] Copy this template to `specs/[feature-name]/tasks.md` in your project. Tasks should be atomic, ordered by dependency, and independently testable.

---

# [Feature/Bugfix Name] — Tasks

**Spec:** [[requirements]] | [[design]]
**Status:** Not started | In progress | Complete

## Task List

### 1. [Task title]

- [ ] **Status:** Not started
- **Description:** [What to do — specific enough that no interpretation is needed]
- **Files:** [Which files to create or modify]
- **Depends on:** None
- **Validates:** [Which requirement or acceptance criterion this satisfies]

### 2. [Task title]

- [ ] **Status:** Not started
- **Description:** [What to do]
- **Files:** [Which files to create or modify]
- **Depends on:** Task 1
- **Validates:** [Which requirement or acceptance criterion this satisfies]

### 3. [Task title]

- [ ] **Status:** Not started
- **Description:** [What to do]
- **Files:** [Which files to create or modify]
- **Depends on:** Task 2
- **Validates:** [Which requirement or acceptance criterion this satisfies]

## Progress

- Total tasks: [N]
- Completed: [0]
- Remaining: [N]

---

> [!tip] **Status markers:** `[ ]` not started, `[-]` in progress, `[x]` complete. Update these as tasks are executed. A good task list has 5-15 tasks. More than 15 suggests the feature should be split into smaller specs.
