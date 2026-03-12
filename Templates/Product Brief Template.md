---
type: template
sdd-version: "0.1"
artifact: product-brief
---

# Product Brief Template

> [!info] Copy this template into your project at `specs/[feature-name]/brief.md`. This is the PO/PM's starting point — capture intent before formal requirements.

---

# [Feature Name] — Product Brief

## Problem Statement

[What user pain, business need, or opportunity are we addressing? Be specific about who is affected and what the current situation is.]

> [!tip] Write from the user's perspective. "Users currently have to contact support to reset their password, which takes 24-48 hours and generates ~200 tickets/month."

## User Need

[Who is the primary user? What do they need to be able to do? What is their current workaround, if any?]

## Success Metrics

[How will we measure whether this feature succeeded? Include at least one quantitative metric.]

- [Metric 1: e.g., "Reduce password reset support tickets by 80%"]
- [Metric 2: e.g., "95% of users complete the reset flow without contacting support"]

> [!tip] If you can't define a success metric, the problem may not be well-understood enough yet. That's okay — list it as an open question below.

## Scope

### In Scope

- [What this feature will do]
- [What this feature will do]

### Out of Scope

- [What this feature explicitly will NOT do]
- [What this feature explicitly will NOT do]

> [!tip] Being explicit about what's out of scope is as important as defining what's in. It prevents scope creep and gives the AI agent clear boundaries.

## Constraints

[Known limitations, deadlines, dependencies, regulatory requirements, or technical constraints that the team must work within.]

- [Constraint 1]
- [Constraint 2]

## Open Questions

[What the PO/PM doesn't know yet and needs answered before or during the Specify phase.]

- [ ] [Question 1]
- [ ] [Question 2]

---

> [!tip] **Next step:** Once this brief is reviewed by the Dev team, expand it into a formal `requirements.md` using the [[Feature Spec Template]]. Delete all `> [!tip]` callouts when you're done filling in the template.
