# Breaking Down Tasks

How to decompose a design into atomic, ordered implementation tasks. Good task decomposition is the difference between smooth AI execution and chaotic back-and-forth.

---

## What Makes a Good Task

Each task should be:

| Property | Meaning | Test |
|----------|---------|------|
| **Atomic** | One logical change | Could you describe it in one sentence? |
| **Ordered** | Dependencies flow forward | Does it only depend on earlier tasks? |
| **Testable** | Independently verifiable | Can you check it works without completing later tasks? |
| **Specific** | No interpretation needed | Would two developers implement it the same way? |
| **Scoped** | Clear file boundaries | Do you know which files are touched? |

---

## Decomposition Strategy

### Start from the Design

Walk through the design document and identify:
1. Data model changes (these come first — everything depends on them)
2. Core business logic (the main feature behavior)
3. Integration points (connecting to existing systems)
4. User-facing components (UI, API endpoints)
5. Error handling and edge cases
6. Tests (can be interleaved or grouped at the end)

### Order by Dependency

A common ordering pattern:
1. Infrastructure / data model setup
2. Core logic / service layer
3. API routes or handlers
4. UI components
5. Integration and wiring
6. Error handling refinement
7. Tests and validation

### Size Check

A well-sized task is roughly **one commit**. If describing the task takes more than 3-4 lines, it's probably too large — split it.

---

## Task Format

Use the [[Task List Template]] format:

```markdown
### 1. Create password reset token table

- [ ] **Status:** Not started
- **Description:** Add a `password_reset_tokens` table with columns:
  id (UUID), user_id (FK), token_hash (varchar), expires_at (timestamp),
  used_at (nullable timestamp). Add index on token_hash.
- **Files:** `src/db/migrations/xxx-create-password-reset-tokens.ts`
- **Depends on:** None
- **Validates:** Requirement 2 (token storage with expiry)
```

---

## Common Mistakes

**Tasks too large:**
- "Implement the password reset feature" — This is the entire spec, not a task
- Split into: create table, create service, create API endpoint, create email template, create UI form, etc.

**Tasks too small:**
- "Add import statement for uuid library" — This isn't a logical unit of work
- Group related micro-changes into one meaningful task

**Missing dependencies:**
- Task 5 modifies a file created in task 3, but doesn't list the dependency
- Always check: does this task assume something from an earlier task?

**Vague descriptions:**
- "Update the API" — Which endpoint? What change? What's the expected behavior?
- Be specific: "Add POST `/api/password-reset/request` endpoint that accepts `{ email: string }` and returns 200 with `{ message: 'If the email is registered...' }`"

---

## Working with AI Agents

When an AI agent helps decompose tasks:
- Provide the full design document as context
- Review the proposed task list before execution
- Check that task order matches dependency flow
- Verify that all requirements are covered (each requirement should map to at least one task)

When an AI agent executes tasks:
- The agent reads the full spec context (steering + spec folder)
- It executes tasks in order, one at a time
- After each task, the developer reviews before proceeding
- If a task reveals a design issue, update the spec — don't hack around it

---

## How Many Tasks?

| Task Count | Signal |
|-----------|--------|
| 1-4 | Very small feature — consider if you even need a spec |
| 5-15 | Sweet spot for most features |
| 15+ | Feature is probably too large — consider splitting into multiple specs |
