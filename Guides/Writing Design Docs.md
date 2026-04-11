# Writing Design Docs

How to write the `design.md` for a feature spec. The design document translates requirements into a technical blueprint that an AI agent can implement.

---

## Purpose

The design document answers: **How will we build this?** It sits between requirements (what to build) and tasks (the work to do). Every design decision should trace back to at least one requirement.

**Owner:** Developer
**Reviewers:** PO/PM (alignment with intent), other developers (technical soundness)

---

## Structure

A design document covers these sections. Include only what's relevant — not every feature needs every section.

### Architecture

How does this feature fit into the existing system? Which components are involved? Draw the high-level picture.

For AI agents, be explicit about:
- Which existing files/modules will be modified
- Which new files/modules will be created
- How new code connects to existing code

### Components

What are the building blocks? For each component:
- **Responsibility** — What it does (single responsibility)
- **Interface** — What goes in, what comes out
- **Dependencies** — What it needs from other components
- **Errors** — What can go wrong and how it's handled

### Data Model

New or modified data structures. Be specific:
- Field names, types, and constraints
- Relationships between entities
- Migration approach for existing data (if applicable)

### API / Interface Contracts

If the feature involves APIs or interfaces:
- Endpoints, methods, request/response shapes
- Authentication/authorization requirements
- Rate limits or quotas
- Error response format

### Error Handling

How errors are detected, reported, and recovered from. Cover:
- Expected error cases and their user-facing messages
- Unexpected errors and fallback behavior
- Retry strategies (if applicable)

### Testing Strategy

What types of tests are needed:
- Unit tests for business logic
- Integration tests for component interactions
- End-to-end tests for user-facing flows
- What specifically each test type should verify

---

## Writing for AI Agents

Design documents are one of the most important context sources for AI agents during implementation. Tips:

**Be explicit about file paths.** "Create a new service" is vague. "Create `src/features/password-reset/reset-service.ts`" is actionable.

**Name existing utilities to reuse.** If there's an existing email sending utility, reference it: "Use the existing `sendEmail()` from `src/lib/email.ts`". This prevents the AI from creating duplicate code.

**Describe interfaces precisely.** AI agents work best when they know exact function signatures, parameter types, and return types.

**State what NOT to do.** "Do not create a new database table — extend the existing `users` table" prevents common AI mistakes.

---

## Design Size

Follow the [[Business/Documentation & Research/Spec driven development/Standard/Principles|smarter specs, not longer specs]] principle:
- A typical design document is 1-2 pages
- If it exceeds 3 pages, consider splitting the feature
- Focus on decisions and interfaces, not implementation details (those belong in the code)

---

## Traceability

Every design decision should connect to a requirement:

| Requirement | Design Decision |
|-------------|----------------|
| "Token expires after 30 minutes" | Store `expires_at` timestamp in the `password_reset_tokens` table |
| "All sessions invalidated on reset" | Call `sessionStore.invalidateAll(userId)` after password update |

If a design decision doesn't trace to a requirement, either:
- There's a missing requirement (add it)
- The decision is unnecessary (remove it)
