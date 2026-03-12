# PO Guide to SDD

How Product Owners and Product Managers use Spec-Driven Development. This guide explains your role, your artifacts, and how to write specs that work for both human developers and AI agents.

---

## Your Role in SDD

As PO/PM, you own the *why* and the *what*. You don't need to understand how the code works — but you need to express what it should do with enough precision that two audiences can act on it:

1. **Human developers** need context, rationale, and the big picture
2. **AI agents** need precision, explicit boundaries, and testable criteria

The good news: writing for AI makes you a better writer for humans too. Vague specs fail with both audiences.

---

## Your Artifacts

### Product Brief (`brief.md`)

Your starting point. Captures the problem, not the solution. Use the [[Product Brief Template]].

**When to write one:**
- The feature involves multiple people (PO + Dev, or PO + Dev + AI)
- The problem needs framing before jumping to requirements
- You want to align stakeholders on *why* before discussing *what*

**When to skip:**
- You're working solo and the requirements are clear in your head
- It's a small enhancement with obvious scope

### Requirements (`requirements.md`)

Your main deliverable. Structured requirements with acceptance criteria. Use the requirements section of the [[Feature Spec Template]].

### Acceptance Criteria

The most important thing you write. Every requirement needs at least one acceptance criterion that is:
- **Binary** — it either passes or fails, no "partially meets"
- **Observable** — you can see or measure the result
- **Independent** — it doesn't secretly depend on another criterion

---

## Writing for Two Audiences

### What humans need that AI doesn't

- **Why** this feature matters (context, user empathy, business rationale)
- **Trade-offs** you considered (helps devs make aligned decisions when ambiguity arises)
- **Priority signals** (what matters most if we can't do everything)

### What AI needs that humans often skip

- **Explicit boundaries** — what the feature must NOT do (humans infer this; AI doesn't)
- **Edge case handling** — what happens when input is invalid, empty, or unexpected
- **Exact formats** — "email" is vague; "valid email per RFC 5322" is precise
- **No assumed context** — everything the AI needs must be written down; it can't ask a colleague

### The sweet spot

Write the *why* and *context* for humans. Write the *what* and *criteria* for AI. Both benefit from both.

> [!example]
> **Objective (for humans):** "Users who forget their password currently contact support, generating ~200 tickets/month. Self-service reset will eliminate most of these."
>
> **Requirement (for AI):** "WHEN a user clicks 'Forgot Password' and enters a registered email, THE SYSTEM SHALL send a password reset email containing a single-use token that expires after 30 minutes."
>
> **Acceptance criterion (for both):** "Given a registered user, when they request a password reset, then they receive an email within 60 seconds containing a link with a valid token."

---

## Your Review Gates

You have three review moments in the SDD [[Workflow]]:

### 1. After Brief → Before Specify

Dev reviews your brief for feasibility. Be open to:
- Scope adjustments (some things may be harder than expected)
- Clarifying questions (your brief will have gaps — that's normal)
- Splitting the feature (one big feature → two focused specs)

### 2. After Design → Before Task

Dev shares their design. Review it for:
- **Alignment with intent** — Does the design solve the actual problem?
- **Missing requirements** — Did the design reveal something you forgot to specify?
- **Scope drift** — Is the design doing more (or less) than what was required?

You don't need to understand every technical detail. Focus on: "If built as described, will this solve the user's problem?"

### 3. After Implement → Validate

Walk through each acceptance criterion:
- Does the implementation actually solve the original problem?
- Would a user be satisfied with this?
- Are there edge cases you didn't think of?

If something's off, update the spec and create new tasks — don't just verbally ask for changes.

---

## Common PO Anti-Patterns in SDD

| Anti-pattern | Problem | Fix |
|-------------|---------|-----|
| "Make it intuitive" | Not testable. AI can't evaluate intuitiveness. | Define specific UX behaviors: "Autocomplete suggestions appear after 2 characters." |
| "Like competitor X" | Requires external research. AI may not know competitor X. | Describe the specific behaviors you want, not where you saw them. |
| "It should be fast" | Not measurable. | "Page loads in under 2 seconds on 3G connection." |
| Assumed context | "Same as the login flow" | Spell out the specific behaviors — the AI doesn't remember other conversations. |
| Scope left open | "And maybe we could also..." | Use the explicit In Scope / Out of Scope sections in the brief. |
| Over-specifying how | "Use React Query for caching" | Unless it's a hard constraint, leave tech decisions to the Dev. |

---

## Choosing a Notation

See [[Writing Requirements]] for full details. Quick guidance:

| Notation | Best for | Example |
|----------|----------|---------|
| **User stories** | Capturing user intent and empathy | "As a forgetful user, I want to reset my password via email" |
| **EARS notation** | Precise system behavior, complex logic | "WHEN the token expires THE SYSTEM SHALL display an error message" |
| **Given/When/Then** | Acceptance criteria, test scenarios | "Given expired token, when user clicks link, then show 'Token expired' message" |
| **Plain language** | Simple, obvious requirements | "The reset email must include the user's first name" |

You can mix notations in a single spec. Use whichever is clearest for each requirement.

---

## Quick Reference

1. Start with a [[Product Brief Template|Product Brief]] (problem, need, metrics, scope)
2. Expand into [[Feature Spec Template|requirements]] with acceptance criteria
3. Review the design for alignment with intent
4. Validate the implementation against your criteria
5. Update the spec if reality changed your understanding

See [[From Story to Spec]] for a step-by-step worked example.
