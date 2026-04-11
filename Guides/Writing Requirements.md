# Writing Requirements

How to write requirements that work for human developers and AI agents. SDD supports multiple notation formats — choose the one that fits each requirement.

---

## The Four Notations

### 1. User Stories

**Best for:** Capturing user intent, building empathy, communicating the "why."

**Format:**
```
As a [role], I want [goal], so that [benefit].
```

**Example:**
```
As a mobile user, I want to scan a QR code to join a meeting,
so that I don't have to type a long meeting URL on my phone.
```

**When to use:**
- The user's perspective is central to the requirement
- You want to communicate why this matters, not just what it does
- The requirement is high-level and will be refined with acceptance criteria

**Limitation:** User stories alone are often too vague for AI agents. Always pair them with specific acceptance criteria.

### 2. EARS Notation

**Best for:** Precise system behavior, complex conditional logic, compliance requirements.

EARS (Easy Approach to Requirements Syntax) uses five patterns:

| Pattern | Template | Use when |
|---------|----------|----------|
| **Ubiquitous** | THE SYSTEM SHALL [behavior] | Behavior that always applies |
| **Event-driven** | WHEN [event] THE SYSTEM SHALL [response] | Behavior triggered by an event |
| **State-driven** | WHILE [state] THE SYSTEM SHALL [behavior] | Behavior that applies during a state |
| **Conditional** | IF [condition] THEN THE SYSTEM SHALL [behavior] | Behavior that depends on a condition |
| **Unwanted** | IF [unwanted condition] THE SYSTEM SHALL [mitigation] | Handling error or edge cases |

**Examples:**
```
WHEN a user uploads a file larger than 10MB
THE SYSTEM SHALL reject the upload and display a message
stating the maximum file size.

WHILE the system is in maintenance mode
THE SYSTEM SHALL redirect all requests to the maintenance page
and return HTTP 503.

IF the payment gateway returns a timeout error
THE SYSTEM SHALL retry the request once after 5 seconds
and display a failure message if the retry also fails.
```

**When to use:**
- System behavior must be unambiguous
- There are multiple conditions or states to handle
- The requirement will be implemented by an AI agent with no further clarification
- Regulatory or compliance requirements that must be precise

### 3. Given/When/Then (Acceptance Criteria)

**Best for:** Defining testable scenarios, specifying expected behavior for specific cases.

**Format:**
```
Given [precondition/context]
When [action/event]
Then [expected outcome]
```

**Example:**
```
Given a user with an expired subscription
When they attempt to access premium content
Then they see an upgrade prompt with their last plan details
And they can still access free content
```

**When to use:**
- Writing acceptance criteria for any requirement (pairs with all other notations)
- Defining test scenarios
- The requirement is best expressed as a specific scenario

### 4. Plain Language

**Best for:** Simple, obvious requirements that don't benefit from formal structure.

**Example:**
```
The password reset email must include the user's first name in the greeting.
The API must return responses in JSON format.
All timestamps must be in UTC.
```

**When to use:**
- The requirement is straightforward and unambiguous without structure
- Adding notation would be ceremony without value

---

## Mixing Notations

You can and should mix notations within a single spec. A common pattern:

1. **User story** — Sets the context and intent
2. **EARS requirements** — Define specific system behaviors
3. **Given/When/Then** — Specify acceptance criteria for each requirement
4. **Plain language** — Capture simple constraints

> [!example]
> **User Story:** As an admin, I want to bulk-invite users via CSV upload, so that I can onboard large teams quickly.
>
> **Requirement (EARS):** WHEN an admin uploads a valid CSV file, THE SYSTEM SHALL create accounts for all listed email addresses and send invitation emails within 5 minutes.
>
> **Acceptance Criteria (Given/When/Then):**
> - Given a CSV with 100 valid emails, when uploaded, then all 100 accounts are created and emails sent
> - Given a CSV with duplicate emails, when uploaded, then duplicates are skipped and a summary is shown
> - Given a CSV with invalid format, when uploaded, then the file is rejected with a specific error message
>
> **Constraint (Plain):** Maximum CSV file size is 1MB. Maximum 500 users per upload.

---

## The Quality Checklist

For every requirement, verify:

- [ ] **Testable** — Can you write a pass/fail check?
- [ ] **Unambiguous** — Would two people interpret it the same way?
- [ ] **Independent** — Does it stand on its own?
- [ ] **Has acceptance criteria** — At least one per requirement
- [ ] **No implementation details** — Says *what*, not *how* (unless it's a hard constraint)

---

## For PO/PMs

See [[Business/Documentation & Research/Spec driven development/Guides/PO Guide to SDD]] for guidance on choosing notations and common anti-patterns. See [[Business/Documentation & Research/Spec driven development/Guides/From Story to Spec]] for a complete worked example.
