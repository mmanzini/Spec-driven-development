# Boundaries

The Always/Ask/Never framework defines explicit constraints on what AI agents and developers should do during implementation. Boundaries exist at two levels: **project-wide** (in the steering document) and **feature-specific** (in the spec's requirements).

---

## The Framework

### Always

Things the AI agent must do without asking. Non-negotiable conventions.

Project-wide examples:
- Follow existing code conventions and naming patterns
- Run tests before marking a task complete
- Write code in the language specified by the steering document
- Keep changes within the scope defined by the current task

Feature-specific examples:
- Validate email format before sending reset link
- Log all authentication attempts
- Use the existing database schema — do not create new tables

### Ask

Things the AI agent must confirm with a human before doing. Decisions requiring judgment.

Project-wide examples:
- Adding a new dependency or library
- Changing a public API contract
- Modifying shared configuration files
- Deviating from the design document

Feature-specific examples:
- Choosing between two valid implementation approaches
- Handling an edge case not covered in requirements
- Modifying a file outside the spec's stated scope

### Never

Things the AI agent must not do. Hard prohibitions.

Project-wide examples:
- Modify environment variables or secrets
- Skip tests or disable linting
- Push directly to main/production branches
- Alter CI/CD pipeline configuration
- Commit files containing credentials

Feature-specific examples:
- Modify unrelated features or components
- Change the database schema without explicit approval
- Downgrade security measures

---

## Where Boundaries Live

| Level | File | Scope |
|-------|------|-------|
| Project-wide | Steering document (`CLAUDE.md`, `.cursorrules`, etc.) | Apply to all work in the project |
| Feature-specific | `requirements.md` (Boundaries section) | Apply only to this feature's implementation |

Feature-specific boundaries **add to** project-wide boundaries — they never override them. If the steering document says "never modify production configs," a feature spec cannot grant permission to do so.

---

## Writing Good Boundaries

**Be specific, not aspirational:**
- Weak: "Be careful with security"
- Strong: "Never store passwords in plaintext; always use bcrypt with a minimum cost factor of 12"

**Be actionable, not philosophical:**
- Weak: "Follow best practices"
- Strong: "Always use parameterized queries for database access"

**Cover the edges:**
- What happens when the AI encounters something not covered by the spec?
- What files or systems are explicitly off-limits?
- What decisions require human approval even if they seem small?

---

## For PO/PMs

Product boundaries are often the most important and the most overlooked. As a PO/PM, define:

- **Data boundaries** — What user data can/cannot be accessed, stored, or modified?
- **Scope boundaries** — What is explicitly out of scope for this feature?
- **Experience boundaries** — What existing user flows must not be disrupted?
- **Compliance boundaries** — What regulatory or policy constraints apply?

These translate directly into the Always/Ask/Never framework and help AI agents stay within the intended scope.
