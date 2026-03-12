# Glossary

Precise definitions of terms used throughout the SDD Standard. When a term appears in other documents, it carries exactly the meaning defined here.

---

| Term | Definition |
|------|-----------|
| **Acceptance Criteria** | Testable conditions that must be true for a requirement to be considered met. Written so that both a human and an AI agent can verify them unambiguously. |
| **AI Agent** | An AI-powered coding assistant (e.g., Claude Code, Cursor, Copilot, Kiro) that executes implementation tasks within the boundaries defined by specs and the steering document. |
| **Boundary** | An explicit constraint on what the AI agent or developer must always do, must ask about, or must never do. See [[Boundaries]]. |
| **Brief** | See *Product Brief*. |
| **Brownfield** | An existing codebase where SDD is being adopted. Contrast with *Greenfield*. |
| **Constitution** | See *Steering Document*. |
| **Design Document** | The `design.md` file within a spec folder. Captures architecture, component interactions, data models, and technical decisions for a specific feature. Owned by the Developer. |
| **EARS Notation** | Easy Approach to Requirements Syntax. A structured format for writing unambiguous requirements using patterns like WHEN/WHILE/IF... THE SYSTEM SHALL... One of several notation options supported by SDD. |
| **Feature Spec** | A set of documents (brief, requirements, design, tasks) in a spec folder that define a single feature from product intent through implementation. |
| **Greenfield** | A new project being built from scratch with SDD. Contrast with *Brownfield*. |
| **Phase Gate** | A review point between workflow phases where a human (PO/PM or Developer) validates the output before proceeding. |
| **Product Brief** | The `brief.md` file within a spec folder. The PO/PM's starting artifact — captures the problem, user need, success metrics, and scope before formal requirements are written. |
| **Product Owner (PO)** | The person responsible for defining *what* to build and *why*. Owns the Product Brief, requirements, acceptance criteria, and final validation of delivered value. |
| **Requirements Document** | The `requirements.md` file within a spec folder. Contains structured requirements and acceptance criteria for a feature. Co-owned by PO/PM (content) and Developer (feasibility review). |
| **Spec** | Short for *specification*. A feature-scoped set of documents (brief, requirements, design, tasks) that define what to build, how to build it, and the work to do. |
| **Spec Folder** | A directory under `specs/` named after the feature or bugfix it describes. Contains all spec documents for that single scope of work. |
| **Steering Document** | The project-level constitution file (e.g., `CLAUDE.md`, `.cursorrules`). Defines project identity, tech stack, coding conventions, and project-wide boundaries. Distinct from feature specs. |
| **Task** | An atomic unit of implementation work defined in `tasks.md`. Scoped small enough to be completed in a single pass — typically one commit. |
| **Task List** | The `tasks.md` file within a spec folder. An ordered sequence of atomic implementation tasks with status tracking and dependency information. |
| **Validation** | The final workflow phase where implementation is checked against requirements and acceptance criteria. PO/PM validates user value; Developer validates technical quality. |
