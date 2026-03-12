# Spec-Driven Development (SDD) Standard

**Version 0.1** | March 2026

Spec-Driven Development is a methodology where structured specifications are the primary artifact guiding software development. Humans define the *what* and *why* through specs; AI agents and developers handle the *how* within clear boundaries. The result: predictable, reviewable, high-quality software — whether built by humans, AI, or both.

SDD bridges the gap between product vision and implementation. It gives Product Owners a structured way to express intent that both developers and AI agents can act on, and gives developers a clear contract to design and build against.

---

## The Standard

- [[Principles]] — The core beliefs that drive SDD
- [[Workflow]] — The 6-phase lifecycle from brief to validation
- [[Roles]] — PO/PM, Developer, and AI Agent responsibilities
- [[Anatomy of a Spec]] — What makes a good spec
- [[Boundaries]] — The Always/Ask/Never framework
- [[Glossary]] — Precise definitions of SDD terms

---

## Templates

Copy these into your project to get started:

- [[Product Brief Template]] — PO/PM starting point before spec creation
- [[Steering Template]] — Project constitution (CLAUDE.md / .cursorrules)
- [[Feature Spec Template]] — New feature specifications
- [[Bugfix Spec Template]] — Bug investigation and fix specifications
- [[Standards Template]] — Project-wide coding conventions
- [[Task List Template]] — Implementation task breakdowns

---

## Guides

- [[Getting Started]] — 5-minute minimal setup
- [[PO Guide to SDD]] — How Product Owners write specs for dev teams and AI
- [[From Story to Spec]] — Translating product vision into SDD artifacts
- [[Writing Requirements]] — Requirements notation guide (multi-format)
- [[Writing Design Docs]] — Design document guide
- [[Breaking Down Tasks]] — Task decomposition guide
- [[Spec Review Checklist]] — Validation checklist
- [[Brownfield Adoption]] — Adopting SDD in an existing codebase
- [[Greenfield Setup]] — Starting a new project with SDD

---

## Examples

Each example uses the exact folder and file structure prescribed by the standard. See [[Examples]] for the full overview.

- **Feature Spec:** `Examples/notification-preferences/` — [[brief|brief]] → [[requirements|requirements]] → [[design|design]] → [[Business Projects/Spec driven development/Examples/notification-preferences/tasks|tasks]]
- **Bugfix Spec:** `Examples/duplicate-order-emails/` — [[bugfix|bugfix]] → [[Business Projects/Spec driven development/Examples/duplicate-order-emails/tasks|tasks]]
- **Steering Doc:** `Examples/taskflow-steering/` — [[Business Projects/Spec driven development/Examples/taskflow-steering/CLAUDE|CLAUDE.md]]

---

## Adoption

- [[Adoption Guide]] — How to adopt SDD incrementally
- [[Tool Agnosticism]] — How SDD works across Claude, Cursor, Copilot, Kiro, and more
