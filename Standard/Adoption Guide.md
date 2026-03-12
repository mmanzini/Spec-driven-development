# Adoption Guide

SDD is designed for incremental adoption. You don't need to implement everything on day one — adopt layer by layer, adding rigor as your needs grow.

---

## Adoption Levels

### Level 1: Steering Only

**Effort:** 15 minutes
**What you do:** Create a steering document at your project root.
**What you get:** AI agents understand your project context, conventions, and boundaries. Every AI interaction improves immediately.

This alone is a significant upgrade over unstructured AI usage.

### Level 2: Steering + Feature Specs

**Effort:** 30-60 minutes per feature
**What you do:** Add `specs/` directory. Write requirements, design, and tasks for complex features.
**What you get:** Predictable, reviewable implementation. Clear handoff between planning and execution.

### Level 3: Full SDD with Product Briefs

**Effort:** Full workflow per feature
**What you do:** PO/PM writes Product Briefs. Full 6-phase [[Workflow]] with review gates.
**What you get:** Clear PO/Dev/AI collaboration model. Product intent preserved through implementation.

### Level 4: Standards Library

**Effort:** Ongoing
**What you do:** Capture project conventions in `standards/` directory.
**What you get:** Consistent code across features and team members. AI agents follow project patterns automatically.

---

## Adoption Path

```
Level 1          Level 2              Level 3              Level 4
Steering    →    + Feature Specs  →   + Product Briefs →   + Standards
(15 min)         (per feature)        (full workflow)       (ongoing)
```

Move to the next level when:
- **Level 1 → 2:** You're building features complex enough that "just start coding" leads to rework
- **Level 2 → 3:** Multiple people are involved in defining what to build (PO + Dev, or multiple stakeholders)
- **Level 3 → 4:** You notice recurring patterns that should be codified

---

## Signals You Need More Structure

| Signal | Suggested Action |
|--------|-----------------|
| AI agent keeps making the same mistakes | Add relevant boundaries to steering document (Level 1) |
| Features get built but don't match what was wanted | Start writing requirements with acceptance criteria (Level 2) |
| PO/PM and Dev have different understanding of the feature | Introduce Product Briefs (Level 3) |
| Code style varies across features | Create coding standards (Level 4) |
| New team members take a long time to get productive | The steering document and standards reduce onboarding time |

## Signals You Have Too Much Structure

| Signal | Suggested Action |
|--------|-----------------|
| Writing specs takes longer than implementing | Use lighter specs — not everything needs EARS notation |
| Team avoids specs because they're a burden | Reduce ceremony — start with just requirements + tasks, skip design for simple features |
| Specs are always outdated after implementation | Enforce the "update the spec" practice in validation, or accept lighter specs |

---

## Tips for Successful Adoption

1. **Start with one person, one feature.** Don't mandate SDD across the team. Let the results speak.
2. **Pick the right first feature.** Medium complexity, upcoming, self-contained. See [[Brownfield Adoption]].
3. **Don't spec everything.** Quick fixes, typo corrections, and exploratory work don't need specs.
4. **Adapt the templates.** The templates are starting points, not rigid forms. Remove sections that don't apply.
5. **Review and iterate.** After 3-5 specs, review what worked and what was unnecessary. Adjust your approach.
