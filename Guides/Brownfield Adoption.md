# Brownfield Adoption

How to adopt SDD in an existing codebase — incrementally, without disrupting ongoing work.

---

## Start Where You Are

You don't need to retroactively spec everything. SDD is adopted **going forward**, one feature at a time.

### Week 1: Steering Document

Create your steering document at the project root. Focus on:
- Project overview (what this is)
- Tech stack (what you use)
- Key commands (build, test, lint)
- 3-5 boundaries (the most important Always/Ask/Never rules)

This alone improves AI-assisted development — the agent now has context about your project.

### Week 2+: First Spec

Pick a feature that's:
- **Medium complexity** — complex enough to benefit from planning, simple enough that spec-writing doesn't feel overwhelming
- **Upcoming** — something you're about to build, not something already built
- **Self-contained** — minimal dependencies on other in-progress work

Create `specs/[feature-name]/` and write requirements, design, and tasks. See [[Business/Documentation & Research/Spec driven development/Guides/Getting Started]] for the step-by-step.

### Ongoing: Build the Habit

After 2-3 features with specs:
- You'll know which parts of SDD help your team most
- You'll develop your own conventions (add them to the steering document)
- You'll recognize when a feature needs a spec vs. when it doesn't

---

## What About Existing Code?

**Don't retroactively spec existing features.** That's busywork with no payoff.

**Do spec when modifying existing features:**
- If you're making significant changes to an existing feature, write a spec for the changes
- Reference the existing code in your design document
- The spec covers the *delta*, not the entire feature

**Do document discovered conventions as standards:**
- If you notice patterns in the existing code, capture them in `standards/[topic].md`
- This helps AI agents follow existing conventions when making changes

---

## Common Challenges

| Challenge | Solution |
|-----------|----------|
| "We don't have a PO" | The person who decides what to build plays the PO role. It might be a developer, tech lead, or founder. |
| "Our codebase is messy" | SDD doesn't require clean code. Specs help you make focused, well-planned changes — which gradually improves the codebase. |
| "We use agile sprints" | SDD fits inside sprints. A spec can be written and executed within a single sprint. Think of it as structured refinement. |
| "Our team is skeptical" | Start with one person, one feature. Let the results speak. Don't mandate — demonstrate. |
| "We already have docs" | Great. Your existing docs may become your steering document or feed into specs. SDD doesn't replace all documentation — it adds structured specs for feature work. |

---

## Integration with Existing Processes

SDD overlaps with — but doesn't replace — these common practices:

| Practice | Relationship to SDD |
|----------|-------------------|
| **Agile user stories** | User stories become one notation option in requirements.md |
| **Technical design docs** | Design docs become design.md in the spec folder |
| **PR descriptions** | Specs provide richer context than PR descriptions; link specs from PRs |
| **ADRs (Architecture Decision Records)** | ADRs cover project-wide decisions; design.md covers feature-specific decisions |
| **JIRA/Linear tickets** | Tickets can reference spec folders; tasks.md provides more detail than ticket descriptions |
