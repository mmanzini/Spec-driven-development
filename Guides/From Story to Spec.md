# From Story to Spec

A step-by-step guide for translating a product idea into a complete SDD spec. Includes a worked example.

---

## The Translation Path

```
Product Idea → Brief → Requirements → Design → Tasks → Implementation
     (PO)       (PO)    (PO + Dev)    (Dev)    (Dev)    (AI + Dev)
```

Each step adds precision. The PO/PM drives the first three steps; the Developer takes over for design and tasks.

---

## Step 1: Start with the Problem

Before writing anything formal, answer these questions:

- **Who** has this problem?
- **What** is the problem? (Describe the pain, not the solution)
- **Why** does it matter now?
- **How** will we know it's solved?

If you can't answer these clearly in conversation, you're not ready to write a spec.

## Step 2: Write the Product Brief

Use the [[Business/Documentation & Research/Spec driven development/Templates/Product Brief Template]]. Capture:
- The problem and who it affects
- What success looks like
- What's in scope and what's out
- What you don't know yet (open questions)

The brief is your thinking tool. It doesn't need to be polished — it needs to be honest about what you know and what you don't.

## Step 3: Expand into Requirements

For each thing the system needs to do, write a requirement with an acceptance criterion.

**Choose your notation per requirement:**
- Use **user stories** when the user's perspective matters
- Use **EARS notation** when system behavior must be precise
- Use **Given/When/Then** for acceptance criteria
- Use **plain language** when the requirement is straightforward

The test: could someone who doesn't know your project read each requirement and understand exactly what to build and how to verify it?

## Step 4: Define Boundaries

What must the implementation always do? What must it ask about? What must it never do?

This is where PO/PMs add the most value for AI agents. Developers think about technical boundaries; PO/PMs think about product, data, and experience boundaries.

## Step 5: Hand Off to Dev

The Developer takes the requirements and:
- Validates feasibility
- Writes the design document
- Breaks the design into tasks
- Executes with AI assistance

Your job shifts to review and validation.

---

## Worked Example: Password Reset

### The Idea

"Users should be able to reset their password themselves instead of contacting support."

### Step 1: The Problem

- **Who:** Registered users who forgot their password
- **What:** They can't log in and must email support, waiting 24-48 hours
- **Why now:** ~200 support tickets/month, 35% of total support volume
- **Success:** 80% reduction in password reset tickets

### Step 2: The Brief

**Problem:** Registered users who forget their password must contact support for a manual reset, generating ~200 tickets/month (35% of support volume). Average resolution time is 24-48 hours.

**User Need:** Users need to reset their password immediately, without waiting for support.

**Success Metrics:**
- Reduce password reset support tickets by 80%
- 95% of users complete the reset flow without contacting support
- Average time from "forgot password" to "logged in" under 5 minutes

**In Scope:** Email-based password reset for registered users.
**Out of Scope:** SMS-based reset, account recovery for unregistered emails, admin password reset.

**Open Questions:**
- What's our email deliverability rate? (May affect success metrics)
- Do we need to support multiple email addresses per account?

### Step 3: The Requirements

**Requirement 1 — User Story:**
As a registered user who forgot my password, I want to reset it via email so that I can regain access to my account without contacting support.

**Acceptance criteria:**
- Given a registered email, when the user requests a reset, then they receive an email within 60 seconds
- Given an unregistered email, when the user requests a reset, then the system shows the same confirmation message (no email enumeration)

**Requirement 2 — EARS:**
WHEN a user submits the password reset form with a registered email, THE SYSTEM SHALL generate a single-use token, store it with a 30-minute expiry, and send an email containing a reset link.

**Acceptance criteria:**
- [ ] Token expires after 30 minutes
- [ ] Token is single-use (invalidated after first use)
- [ ] Email contains a direct link to the reset page with the token embedded

**Requirement 3 — EARS:**
WHEN a user submits a new password via a valid reset link, THE SYSTEM SHALL update the password, invalidate the token, invalidate all existing sessions, and redirect to the login page.

**Acceptance criteria:**
- [ ] New password must meet existing password policy
- [ ] All existing sessions for the user are terminated
- [ ] User can log in with the new password immediately

**Requirement 4 — EARS (unwanted behavior):**
IF a user submits a new password via an expired or already-used token, THE SYSTEM SHALL display an error message and offer to resend the reset email.

### Step 4: The Boundaries

**Always:**
- Rate-limit reset requests to 3 per email per hour
- Use the same confirmation message for registered and unregistered emails

**Never:**
- Never reveal whether an email is registered (prevent enumeration)
- Never store the token in plaintext
- Never send the password itself via email

---

## Key Takeaways

1. **Start vague, get precise** — The brief is intentionally loose; requirements are intentionally tight
2. **One requirement, one behavior** — Don't bundle multiple behaviors into a single requirement
3. **Acceptance criteria are the contract** — If it's not in the criteria, it's not required; if it is, it must be verified
4. **Boundaries prevent surprises** — Especially important for AI agents that will take your spec literally
5. **The PO owns steps 1-4; the Dev owns what comes after** — Clear handoff, clear ownership
