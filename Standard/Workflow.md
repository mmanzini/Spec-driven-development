# Workflow

The SDD lifecycle has six phases, from product intent to validated implementation. Each phase has a clear owner, defined inputs and outputs, and a review gate before proceeding.

---

## Overview

```
Brief → Specify → Design → Task → Implement → Validate
 (PO)   (PO+Dev)  (Dev)   (Dev+AI)  (AI+Dev)   (PO+Dev)
```

Two entry points are supported:
- **Requirements-First** (default): Start at Phase 0 (Brief). PO-driven. Best for product-led development.
- **Design-First**: Start at Phase 2 (Design), then derive requirements. Dev-driven. Best when architecture is the primary constraint (porting, compliance, technical migration).

---

## Phase 0: Brief

**Owner:** PO/PM
**Input:** A product idea, user problem, or business need
**Output:** `brief.md`

The PO writes a [[Business/Documentation & Research/Spec driven development/Templates/Product Brief Template|Product Brief]] capturing:
- The problem being solved and who it affects
- What success looks like (measurable where possible)
- What's in scope and what's explicitly out
- Known constraints and open questions

The brief is intentionally non-technical. It captures *intent*, not implementation. It's the starting point — not the final spec.

**Review gate:** Dev reviews the brief for feasibility and asks clarifying questions before proceeding.

---

## Phase 1: Specify

**Owner:** PO/PM (content) + Developer (feasibility review)
**Input:** `brief.md`
**Output:** `requirements.md`

Transform the brief into structured requirements with acceptance criteria. The PO writes the *what*; the Developer validates that each requirement is technically feasible.

Requirements can use any supported notation — see [[Business/Documentation & Research/Spec driven development/Guides/Writing Requirements]]:
- **User stories** for capturing user intent and empathy
- **EARS notation** for precise system behavior
- **Acceptance criteria (Given/When/Then)** for testable conditions
- **Freeform requirements** for straightforward needs

Every requirement must have at least one acceptance criterion. If you can't write a test for it, the requirement is too vague.

**Review gate:** PO and Dev agree that requirements are complete, feasible, and testable.

---

## Phase 2: Design

**Owner:** Developer
**Input:** `requirements.md`
**Output:** `design.md`

The Developer writes the technical design covering:
- Architecture decisions and component interactions
- Data models and state management
- API contracts and integration points
- Error handling strategy
- Testing approach

The design must trace back to requirements — every design decision should serve at least one requirement. Design decisions without a corresponding requirement indicate either a missing requirement or unnecessary complexity.

**Review gate:** PO reviews for alignment with original intent. Dev validates technical soundness.

---

## Phase 3: Task

**Owner:** Developer + AI Agent (assistant)
**Input:** `design.md`
**Output:** `tasks.md`

Break the design into an ordered list of atomic implementation tasks. Each task should be:
- **One logical change** — typically one commit
- **Independently testable** — you can verify it works without completing later tasks
- **Sequenced by dependency** — tasks that depend on earlier work come later
- **Clear in scope** — the task description leaves no room for interpretation

The AI agent can help decompose the design into tasks, but the Developer validates the breakdown. See [[Business/Documentation & Research/Spec driven development/Guides/Breaking Down Tasks]].

Each task in `tasks.md` tracks status: `[ ]` not started, `[-]` in progress, `[x]` complete.

**Review gate:** Dev confirms the task list fully covers the design.

---

## Phase 4: Implement

**Owner:** AI Agent + Developer (reviewer)
**Input:** `tasks.md` + `design.md` + `requirements.md` + steering document
**Output:** Working code

The AI agent reads the full spec context and executes tasks in order. The Developer reviews output after each task (or batch of tasks, depending on trust level and complexity).

During implementation:
- The spec is the primary instruction set for the AI agent
- If the agent encounters ambiguity, it flags it rather than guessing
- If implementation reveals a design issue, **update the spec** — don't silently diverge
- [[Business/Documentation & Research/Spec driven development/Standard/Boundaries]] define what the agent must always do, must ask about, and must never do

---

## Phase 5: Validate

**Owner:** PO/PM + Developer
**Input:** Completed implementation + `requirements.md`
**Output:** Validated feature or identified gaps

Walk through each requirement and verify it is met:
- **PO/PM validates user value**: Does the implementation solve the original problem? Do acceptance criteria pass?
- **Developer validates technical quality**: Does the code meet standards? Are there regressions?

If validation reveals gaps:
- Update the spec to reflect what was learned
- Create new tasks for remaining work
- Re-enter the workflow at the appropriate phase

---

## The Portable Spec Structure

Any project adopting SDD uses this folder structure:

```
project-root/
  CLAUDE.md (or .cursorrules, etc.)   # Steering document
  specs/
    [feature-name]/
      brief.md                        # (optional) Product Brief — PO/PM starting point
      requirements.md                 # Structured requirements + acceptance criteria
      design.md                       # Architecture & design decisions
      tasks.md                        # Ordered atomic tasks
      research.md                     # (optional) Alternatives explored
    [bugfix-name]/
      bugfix.md                       # Current vs expected vs unchanged behavior
      tasks.md                        # Fix implementation tasks
  standards/                          # (optional) Project-wide coding conventions
    [topic].md
```

**Naming conventions:**
- Spec folders use hyphenated slugs: `user-authentication/`, `payment-processing/`
- `specs/` is visible and version-controlled, not hidden (no `.specs/` or `.kiro/`)
- The steering document filename is tool-specific (`CLAUDE.md`, `.cursorrules`, etc.) but follows the [[Business/Documentation & Research/Spec driven development/Templates/Steering Template|SDD content structure]]

---

## When to Use SDD

SDD is for work that benefits from structured planning:
- Features requiring multiple components or integration points
- Bugs where regressions are costly
- Work involving PO/Dev/AI collaboration
- Any task where "just start coding" leads to rework

For quick fixes, typo corrections, or exploratory prototyping — skip the ceremony and just do it. You can always generate a spec retroactively if the work grows in scope.
