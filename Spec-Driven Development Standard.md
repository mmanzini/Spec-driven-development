# Spec-Driven Development (SDD) Standard

**Version 0.1** | March 2026

Spec-Driven Development is a methodology where structured specifications are the primary artifact guiding software development. Humans define the *what* and *why* through specs; AI agents and developers handle the *how* within clear boundaries. The result: predictable, reviewable, high-quality software — whether built by humans, AI, or both.

SDD bridges the gap between product vision and implementation. It gives Product Owners a structured way to express intent that both developers and AI agents can act on, and gives developers a clear contract to design and build against.

---

## The Standard

- [[Business/Documentation & Research/Spec driven development/Standard/Principles]] — The core beliefs that drive SDD
- [[Business/Documentation & Research/Spec driven development/Standard/Workflow]] — The 6-phase lifecycle from brief to validation
- [[Business/Documentation & Research/Spec driven development/Standard/Roles]] — PO/PM, Developer, and AI Agent responsibilities
- [[Business/Documentation & Research/Spec driven development/Standard/Anatomy of a Spec]] — What makes a good spec
- [[Business/Documentation & Research/Spec driven development/Standard/Boundaries]] — The Always/Ask/Never framework
- [[Business/Documentation & Research/Spec driven development/Standard/Glossary]] — Precise definitions of SDD terms

---

## Templates

Copy these into your project to get started:

- [[Business/Documentation & Research/Spec driven development/Templates/Product Brief Template]] — PO/PM starting point before spec creation
- [[Business/Documentation & Research/Spec driven development/Templates/Steering Template]] — Project constitution (CLAUDE.md / .cursorrules)
- [[Business/Documentation & Research/Spec driven development/Templates/Feature Spec Template]] — New feature specifications
- [[Business/Documentation & Research/Spec driven development/Templates/Bugfix Spec Template]] — Bug investigation and fix specifications
- [[Business/Documentation & Research/Spec driven development/Templates/Standards Template]] — Project-wide coding conventions
- [[Business/Documentation & Research/Spec driven development/Templates/Task List Template]] — Implementation task breakdowns

---

## Guides

- [[Business/Documentation & Research/Spec driven development/Guides/Getting Started]] — 5-minute minimal setup
- [[Business/Documentation & Research/Spec driven development/Guides/PO Guide to SDD]] — How Product Owners write specs for dev teams and AI
- [[Business/Documentation & Research/Spec driven development/Guides/From Story to Spec]] — Translating product vision into SDD artifacts
- [[Business/Documentation & Research/Spec driven development/Guides/Writing Requirements]] — Requirements notation guide (multi-format)
- [[Business/Documentation & Research/Spec driven development/Guides/Writing Design Docs]] — Design document guide
- [[Business/Documentation & Research/Spec driven development/Guides/Breaking Down Tasks]] — Task decomposition guide
- [[Business/Documentation & Research/Spec driven development/Guides/Spec Review Checklist]] — Validation checklist
- [[Business/Documentation & Research/Spec driven development/Guides/Brownfield Adoption]] — Adopting SDD in an existing codebase
- [[Business/Documentation & Research/Spec driven development/Guides/Greenfield Setup]] — Starting a new project with SDD

---

## Examples

Each example uses the exact folder and file structure prescribed by the standard. See [[Business/Documentation & Research/Spec driven development/Examples/Examples]] for the full overview.

- **Feature Spec:** `Examples/notification-preferences/` — [[Business/Documentation & Research/Spec driven development/Examples/notification-preferences/brief|brief]] → [[Business/Documentation & Research/Spec driven development/Examples/notification-preferences/requirements|requirements]] → [[Business/Documentation & Research/Spec driven development/Examples/notification-preferences/design|design]] → [[Business Projects/Spec driven development/Examples/notification-preferences/tasks|tasks]]
- **Bugfix Spec:** `Examples/duplicate-order-emails/` — [[Business/Documentation & Research/Spec driven development/Examples/duplicate-order-emails/bugfix|bugfix]] → [[Business Projects/Spec driven development/Examples/duplicate-order-emails/tasks|tasks]]
- **Steering Doc:** `Examples/taskflow-steering/` — [[Business Projects/Spec driven development/Examples/taskflow-steering/CLAUDE|CLAUDE.md]]

---

## Adoption

- [[Business/Documentation & Research/Spec driven development/Standard/Adoption Guide]] — How to adopt SDD incrementally
- [[Business/Documentation & Research/Spec driven development/Standard/Tool Agnosticism]] — How SDD works across Claude, Cursor, Copilot, Kiro, and more
