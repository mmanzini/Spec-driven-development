---
type: template
sdd-version: "0.1"
artifact: feature-spec
---

# Feature Spec Template

> [!info] This template covers all three core spec files for a feature. Create a folder at `specs/[feature-name]/` and split this into separate files: `requirements.md`, `design.md`, and `tasks.md`. Optionally start with a `brief.md` using the [[Product Brief Template]].

---

## requirements.md

# [Feature Name] — Requirements

## Objective

[One paragraph: what problem does this solve and why now? Reference the Product Brief if one exists.]

## Requirements

> [!tip] Choose the notation that fits each requirement. You can mix notations within a single spec. See [[Writing Requirements]] for guidance on when to use each format.

### User Stories

As a [role], I want [goal], so that [benefit].

**Acceptance criteria:**
- Given [context], when [action], then [outcome]
- Given [context], when [action], then [outcome]

### System Behavior

WHEN [trigger event]
THE SYSTEM SHALL [expected response]

**Acceptance criteria:**
- [ ] [Testable criterion]

### Conditional Requirements

IF [condition]
THEN THE SYSTEM SHALL [behavior]

**Acceptance criteria:**
- [ ] [Testable criterion]

## Boundaries

### Always
- [Feature-specific things the implementation must always do]

### Ask
- [Feature-specific things requiring human confirmation]

### Never
- [Feature-specific prohibitions]

## Acceptance Criteria Summary

- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

---

## design.md

# [Feature Name] — Design

## Architecture

[How does this feature fit into the existing system? Which components are involved?]

## Components

[What new or modified components are needed? Define their responsibilities and interfaces.]

### [Component Name]

**Responsibility:** [What it does]
**Input:** [What it receives]
**Output:** [What it produces]
**Errors:** [What can go wrong]

## Data Model

[New or modified data structures, database tables, API contracts.]

## Integration Points

[How this feature connects to existing systems, external APIs, or other features.]

## Error Handling

[How errors are detected, reported, and recovered from.]

## Testing Strategy

[What types of tests are needed and what they verify.]

---

## tasks.md

# [Feature Name] — Tasks

## Task List

> [!tip] Tasks should be atomic (one logical change), ordered by dependency, and independently testable. Mark status as: `[ ]` not started, `[-]` in progress, `[x]` complete.

### 1. [Task title]

- [ ] **Status:** Not started
- **Description:** [What to do, specifically]
- **Files:** [Which files to create or modify]
- **Validates:** [Which requirement/acceptance criterion this satisfies]

### 2. [Task title]

- [ ] **Status:** Not started
- **Description:** [What to do, specifically]
- **Files:** [Which files to create or modify]
- **Depends on:** Task 1
- **Validates:** [Which requirement/acceptance criterion this satisfies]

### 3. [Task title]

- [ ] **Status:** Not started
- **Description:** [What to do, specifically]
- **Files:** [Which files to create or modify]
- **Depends on:** Task 2
- **Validates:** [Which requirement/acceptance criterion this satisfies]

---

> [!tip] Delete all `> [!tip]` callouts and replace all `[BRACKETS]` with your actual content. See [[Anatomy of a Spec]] for quality guidelines.
