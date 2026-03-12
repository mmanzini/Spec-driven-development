# Spec Review Checklist

Use this checklist to validate a spec before moving to implementation. Review at each phase gate in the [[Workflow]].

---

## After Brief (Phase 0 → Phase 1)

- [ ] Problem is clearly stated from the user's perspective
- [ ] Success metrics are defined and measurable
- [ ] Scope boundaries are explicit (in scope and out of scope)
- [ ] Open questions are listed (not hidden assumptions)
- [ ] Developer has reviewed for feasibility

## After Requirements (Phase 1 → Phase 2)

- [ ] Every requirement has at least one acceptance criterion
- [ ] Acceptance criteria are testable (pass/fail, not subjective)
- [ ] No implicit assumptions — everything needed is written down
- [ ] Requirements describe *what*, not *how*
- [ ] Boundaries are defined (Always/Ask/Never)
- [ ] No duplicate or contradictory requirements
- [ ] A developer unfamiliar with the project could understand what to build
- [ ] An AI agent could implement without asking clarifying questions

## After Design (Phase 2 → Phase 3)

- [ ] Every design decision traces to at least one requirement
- [ ] No design decision exists without a corresponding requirement
- [ ] File paths and component names are specific
- [ ] Existing utilities and patterns are referenced (no unnecessary new code)
- [ ] Error handling is covered
- [ ] Testing strategy is defined
- [ ] PO/PM confirms design aligns with product intent

## After Tasks (Phase 3 → Phase 4)

- [ ] Tasks are atomic (one logical change each)
- [ ] Tasks are ordered by dependency
- [ ] Every task lists which files it touches
- [ ] Every task references which requirement it satisfies
- [ ] All requirements are covered by at least one task
- [ ] Task count is between 5-15 (if not, reconsider scope)
- [ ] A developer could execute each task without ambiguity

## After Implementation (Phase 4 → Phase 5)

- [ ] Every acceptance criterion has been verified
- [ ] No requirements were skipped or only partially implemented
- [ ] Boundaries were respected (check Always/Ask/Never compliance)
- [ ] Spec was updated if implementation revealed new information
- [ ] PO/PM validates the feature solves the original problem
- [ ] Developer validates technical quality and absence of regressions
