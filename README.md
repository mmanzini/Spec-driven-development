# Spec-Driven Development (SDD) Standard

**Version 0.1** · March 2026

Spec-Driven Development is a methodology where structured specifications are the primary artifact guiding software development. Humans define the *what* and *why* through specs; AI agents and developers handle the *how* within clear boundaries.

The result: predictable, reviewable, high-quality software — whether built by humans, AI, or both.

---

## Why SDD?

AI coding agents are powerful executors. They are not product managers, architects, or decision-makers. Without structure, AI-assisted development produces code that requires constant course-correction and rework.

SDD solves this by making the specification the contract. The agent reads the spec, executes within its boundaries, and flags ambiguity rather than guessing. The spec — not the chat history — is the source of truth.

---

## The Workflow

```
Brief → Specify → Design → Task → Implement → Validate
 (PO)   (PO+Dev)  (Dev)   (Dev+AI)  (AI+Dev)   (PO+Dev)
```

Six phases, each with a clear owner and a review gate before proceeding:

| Phase | Owner | Output |
|-------|-------|--------|
| **Brief** | PO/PM | `brief.md` — problem, success metrics, scope |
| **Specify** | PO/PM + Dev review | `requirements.md` — structured requirements + acceptance criteria |
| **Design** | Developer | `design.md` — architecture, data models, API contracts |
| **Task** | Developer + AI assist | `tasks.md` — ordered, atomic implementation tasks |
| **Implement** | AI Agent + Dev review | Working code, one task at a time |
| **Validate** | PO/PM + Developer | Implementation verified against requirements |

---

## Spec Folder Structure

Any project adopting SDD uses this layout:

```
project-root/
  CLAUDE.md (or .cursorrules, etc.)   # Steering document
  specs/
    [feature-name]/
      brief.md          # Product intent (optional)
      requirements.md   # Structured requirements + acceptance criteria
      design.md         # Architecture & design decisions
      tasks.md          # Ordered atomic tasks with status tracking
    [bugfix-name]/
      bugfix.md         # Current vs expected vs unchanged behavior
      tasks.md          # Fix implementation tasks
  standards/            # Project-wide coding conventions (optional)
    [topic].md
```

---

## Tool Agnostic

Specs are plain Markdown files. SDD works with any AI coding tool:

| Tool | Steering Document |
|------|------------------|
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursorrules` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Kiro | Project-level context (spec format is natively compatible) |
| Windsurf, others | Any readable Markdown file |

If your AI tool changes tomorrow, your specs remain valuable — as documentation, as context for the next tool, and as a record of decisions made.

---

## What's in This Repository

### 📐 [The Standard](Standard/)

- [Principles](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Principles.md) — The 10 core beliefs behind SDD
- [Workflow](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Workflow.md) — The 6-phase lifecycle in detail
- [Roles](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Roles.md) — PO/PM, Developer, and AI Agent responsibilities
- [Anatomy of a Spec](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Anatomy%20of%20a%20Spec.md) — What makes a good spec
- [Boundaries](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Boundaries.md) — The Always/Ask/Never framework for AI agents
- [Glossary](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Glossary.md) — Precise definitions of SDD terms
- [Tool Agnosticism](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Tool%20Agnosticism.md) — How SDD maps to Claude, Cursor, Copilot, Kiro, and more
- [Adoption Guide](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Adoption%20Guide.md) — Incremental adoption path

### 📋 [Templates](Templates/)

Copy these into your project:

- [Product Brief Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Product%20Brief%20Template.md) — PO/PM starting point
- [Steering Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Steering%20Template.md) — Project constitution (`CLAUDE.md` / `.cursorrules`)
- [Feature Spec Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Feature%20Spec%20Template.md) — New feature specifications
- [Bugfix Spec Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Bugfix%20Spec%20Template.md) — Bug investigation and fix specs
- [Standards Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Standards%20Template.md) — Project-wide coding conventions
- [Task List Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Task%20List%20Template.md) — Implementation task breakdowns

### 📖 [Guides](Guides/)

- [Getting Started](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/Getting%20Started.md) — 5-minute minimal setup
- [PO Guide to SDD](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/PO%20Guide%20to%20SDD.md) — How Product Owners write specs for dev teams and AI
- [From Story to Spec](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/From%20Story%20to%20Spec.md) — Translating product vision into SDD artifacts
- [Writing Requirements](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/Writing%20Requirements.md) — Requirements notation guide (user stories, EARS, Given/When/Then)
- [Writing Design Docs](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/Writing%20Design%20Docs.md) — Design document guide
- [Breaking Down Tasks](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/Breaking%20Down%20Tasks.md) — Task decomposition guide
- [Spec Review Checklist](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/Spec%20Review%20Checklist.md) — Validation checklist
- [Greenfield Setup](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/Greenfield%20Setup.md) — Starting a new project with SDD
- [Brownfield Adoption](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/Brownfield%20Adoption.md) — Adopting SDD in an existing codebase

### 🗂️ [Examples](Examples/)

Fully worked examples using the exact SDD folder structure:

- **Feature Spec:** [`Examples/notification-preferences/`](Examples/notification-preferences/) — brief → requirements → design → tasks
- **Bugfix Spec:** [`Examples/duplicate-order-emails/`](Examples/duplicate-order-emails/) — bugfix → tasks
- **Steering Document:** [`Examples/taskflow-steering/`](Examples/taskflow-steering/) — CLAUDE.md example

---

## Quick Start

**If you're a developer or team lead:**

1. Copy [Steering Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Steering%20Template.md) → `CLAUDE.md` at your project root
2. Fill in your tech stack, conventions, and boundaries
3. When starting a feature, copy [Feature Spec Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Feature%20Spec%20Template.md) → `specs/[feature-name]/`

**If you're a Product Owner:**

Start with the [PO Guide to SDD](Business/Documentation%20&%20Research/Spec%20driven%20development/Guides/PO%20Guide%20to%20SDD.md) and the [Product Brief Template](Business/Documentation%20&%20Research/Spec%20driven%20development/Templates/Product%20Brief%20Template.md).

**If you want to adopt incrementally:**

Read the [Adoption Guide](Business/Documentation%20&%20Research/Spec%20driven%20development/Standard/Adoption%20Guide.md). You don't need to adopt the full standard on day one.

---

## Core Principles (Summary)

1. **Specs Before Code** — Time invested in specification reduces total implementation time
2. **Feature-Scoped** — One spec folder per feature; never a monolithic spec
3. **The Constitution Is Not a Spec** — Steering documents and feature specs are distinct
4. **Smarter Specs, Not Longer Specs** — Precise and testable beats verbose and vague
5. **Portable Across Tools** — Plain Markdown, no vendor lock-in
6. **Incremental Adoption** — Layer in the standard at your own pace
7. **Living Documents** — Update the spec when reality diverges from the plan
8. **Human Decides, AI Executes** — The agent flags ambiguity; humans make decisions
9. **Validate Against the Spec** — Acceptance criteria become test cases
10. **Product Intent Drives Specs** — The PO owns the why; the spec bridges intent and implementation

---

## Status

This standard is at **version 0.1** — stable enough to use, actively refined based on real-world adoption. Feedback and contributions welcome.

---

*Spec-Driven Development Standard — a public, tool-agnostic methodology for structured software development with AI coding agents.*
