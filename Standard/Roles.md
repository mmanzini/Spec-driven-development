# Roles

SDD defines three actors with distinct responsibilities. Clear ownership prevents gaps (nobody owns it) and conflicts (everybody owns it).

---

## Product Owner / Product Manager

The PO/PM is the voice of the user and the business. They own the *why* and the *what*.

**Responsibilities:**
- Write the [[Business/Documentation & Research/Spec driven development/Templates/Product Brief Template|Product Brief]] — the starting artifact that captures problem, need, and success metrics
- Author and approve requirements in `requirements.md`
- Define acceptance criteria that are testable by both humans and AI agents
- Review design documents for alignment with product intent (not technical correctness)
- Validate the final implementation against requirements — does it solve the original problem?

**Key skill in SDD:** Writing for two audiences simultaneously. Human developers need context, narrative, and rationale. AI agents need precision, explicit boundaries, and testable criteria. A good SDD requirement serves both.

**Phase ownership:**

| Phase | PO/PM Role |
|-------|-----------|
| Brief | **Owns** — writes the Product Brief |
| Specify | **Owns** — writes requirements; Dev reviews feasibility |
| Design | Reviews — checks alignment with intent |
| Task | Informed — may clarify scope questions |
| Implement | Informed — available for clarification |
| Validate | **Owns** — validates user value and acceptance criteria |

**Common anti-patterns to avoid:**
- Vague acceptance criteria ("it should be fast" → "page loads in under 2 seconds")
- Assumed context ("like we did last time" → spell it out; AI agents have no memory of last time)
- Scope creep via ambiguity ("and maybe also..." → define explicit scope boundaries)
- Over-specifying the *how* (leave technical decisions to the Developer)

---

## Developer

The Developer owns the *how*. They translate requirements into architecture and code.

**Responsibilities:**
- Review the Product Brief and requirements for technical feasibility
- Write the design document (`design.md`) — architecture, components, data models, API contracts
- Break the design into atomic tasks (`tasks.md`)
- Review AI-generated code for quality, correctness, and adherence to standards
- Maintain the [[Business/Documentation & Research/Spec driven development/Templates/Steering Template|steering document]] with project-wide conventions
- Validate technical quality during the Validate phase

**Phase ownership:**

| Phase | Developer Role |
|-------|---------------|
| Brief | Reviews — flags feasibility concerns |
| Specify | Reviews — validates feasibility of each requirement |
| Design | **Owns** — writes design.md |
| Task | **Owns** — writes tasks.md (AI may assist) |
| Implement | Reviews — validates AI output per task |
| Validate | **Owns** — validates technical quality |

---

## AI Agent

The AI agent is a powerful executor that works within boundaries. It does not make product or architectural decisions.

**Responsibilities:**
- Read the full spec context (steering document + spec folder) before starting work
- Execute tasks in the order defined in `tasks.md`
- Follow the [[Business/Documentation & Research/Spec driven development/Standard/Boundaries|Always/Ask/Never]] framework strictly
- Flag ambiguity or contradictions rather than guessing
- Produce code that is reviewable in small, task-sized increments

**What the AI agent should never do:**
- Make product decisions (that's the PO/PM)
- Make architectural decisions not covered by the design (that's the Developer)
- Skip tasks or change task order without human approval
- Modify files outside the scope defined in the spec
- Assume context that isn't explicitly stated in the spec or steering document

**The spec is the agent's primary instruction set.** The steering document provides project-wide rules; the spec folder provides feature-specific context. Together, they give the agent everything it needs to execute correctly.

---

## Collaboration Model

```
PO/PM                Developer              AI Agent
  │                      │                      │
  ├─ Brief ─────────────►│                      │
  │                      │                      │
  ├─ Requirements ──────►│                      │
  │  (Dev reviews)       │                      │
  │                      ├─ Design              │
  │  (PO reviews)◄───────┤                      │
  │                      │                      │
  │                      ├─ Tasks ─────────────►│
  │                      │                      │
  │                      │◄── Implementation ───┤
  │                      │   (Dev reviews)      │
  │                      │                      │
  ├─ Validation ◄────────┤                      │
  │  (PO: value)         │  (Dev: quality)      │
```

Each handoff is a review gate. No phase proceeds without the responsible party's approval.
