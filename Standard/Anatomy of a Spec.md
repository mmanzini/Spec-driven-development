# Anatomy of a Spec

What makes a good spec? This document defines the six areas every feature spec should cover and explains what quality looks like in each.

---

## The Six Areas

A complete feature spec addresses these areas across its documents (`brief.md`, `requirements.md`, `design.md`, `tasks.md`):

### 1. Objective and Purpose

**Where:** `brief.md` and the opening section of `requirements.md`
**Owner:** PO/PM

What problem does this feature solve? Why now? What does success look like?

A good objective is:
- **Specific** — names the user and the problem
- **Measurable** — includes success criteria that can be verified
- **Bounded** — states what's in scope and what's out

> [!example]
> **Weak:** "Improve the login experience."
> **Strong:** "Allow users who forgot their password to reset it via email, reducing support tickets for password resets by 80%."

### 2. Requirements

**Where:** `requirements.md`
**Owner:** PO/PM (content) + Developer (feasibility)

Structured statements of what the system should do. See [[Business/Documentation & Research/Spec driven development/Guides/Writing Requirements]] for notation options.

A good requirement is:
- **Testable** — you can write a pass/fail check for it
- **Independent** — it doesn't secretly depend on another unstated requirement
- **Unambiguous** — two people reading it would agree on what it means
- **Necessary** — removing it would leave the feature incomplete

Every requirement must have at least one acceptance criterion.

### 3. Design Decisions

**Where:** `design.md`
**Owner:** Developer

How will the feature be built? Architecture, component interactions, data models, API surface.

A good design:
- **Traces to requirements** — every decision serves at least one requirement
- **Records alternatives considered** — especially when the choice is non-obvious
- **Defines interfaces** — what goes in, what comes out, what errors are possible
- **Considers edge cases** — what happens when things go wrong

### 4. Constraints and Boundaries

**Where:** Spread across `requirements.md` (feature-specific) and the steering document (project-wide)
**Owner:** PO/PM (product constraints) + Developer (technical constraints)

What the implementation must do, must ask about, and must never do. See [[Business/Documentation & Research/Spec driven development/Standard/Boundaries]] for the Always/Ask/Never framework.

Constraints include:
- Performance requirements
- Security requirements
- Compatibility requirements
- Dependencies that must or must not be used
- Files or systems that must not be modified

### 5. Task Decomposition

**Where:** `tasks.md`
**Owner:** Developer (+ AI Agent as assistant)

The ordered sequence of atomic work items. See [[Business/Documentation & Research/Spec driven development/Guides/Breaking Down Tasks]].

Good tasks are:
- **Atomic** — one logical change per task
- **Ordered** — dependencies flow forward, never backward
- **Testable** — each can be verified independently
- **Specific** — no interpretation needed; the task describes exactly what to do

### 6. Validation Criteria

**Where:** Acceptance criteria in `requirements.md`, verification steps in `tasks.md`
**Owner:** PO/PM (user value) + Developer (technical quality)

How do we know it's done? This is not an afterthought — it's the bridge between specifying and validating.

Good validation criteria:
- Map 1:1 to requirements
- Are written before implementation begins
- Are executable (manually or automatically)
- Cover both happy paths and error cases

---

## The Quality Test

A spec is ready for implementation when:

1. A developer who has never seen the project could read the spec and understand what to build
2. An AI agent could read the spec and execute tasks without needing to ask clarifying questions
3. After implementation, you could verify every requirement by checking its acceptance criteria
4. There are no implicit assumptions — everything the implementer needs to know is written down

If any of these fail, the spec needs more work before proceeding to implementation.

---

## Spec Size

Follow the [[Business/Documentation & Research/Spec driven development/Standard/Principles|smarter specs, not longer specs]] principle:

- A typical feature spec is **2-4 pages** across all documents combined
- If your requirements document exceeds 2 pages, consider splitting the feature into smaller specs
- If your task list exceeds 15 tasks, the feature may be too large for a single spec
- Every sentence should earn its place — if removing it wouldn't change the implementation, remove it
