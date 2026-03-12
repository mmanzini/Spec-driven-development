# Examples

Fully worked examples demonstrating the SDD standard in practice. Each example mirrors the exact file structure that a real project would use.

---

## Feature Spec Example: Notification Preferences

A complete feature spec for a fictional **TaskFlow** application (see [[CLAUDE|TaskFlow steering document]]). Demonstrates the full 6-phase workflow from Product Brief through implementation tasks.

**Folder structure:**
```
Examples/notification-preferences/
  brief.md            ← PO/PM starting artifact
  requirements.md     ← Structured requirements + acceptance criteria
  design.md           ← Architecture and technical design
  tasks.md            ← Ordered atomic implementation tasks
```

**Files:**
- [[brief|brief.md]] — Product Brief capturing user problem, success metrics, scope
- [[requirements|requirements.md]] — 5 requirements using mixed notation (user stories + EARS), with acceptance criteria and boundaries
- [[design|design.md]] — Component architecture, data model, API contracts, error handling
- [[Business Projects/Spec driven development/Examples/notification-preferences/tasks|tasks.md]] — 7 ordered tasks with dependencies and requirement traceability

---

## Bugfix Spec Example: Duplicate Order Emails

A bugfix spec for a duplicate email sending issue. Demonstrates the bugfix variant with current/expected/unchanged behavior analysis.

**Folder structure:**
```
Examples/duplicate-order-emails/
  bugfix.md           ← Bug analysis (replaces requirements.md)
  tasks.md            ← Fix implementation tasks
```

**Files:**
- [[bugfix|bugfix.md]] — Bug summary, reproduction steps, root cause analysis, proposed fix, boundaries
- [[Business Projects/Spec driven development/Examples/duplicate-order-emails/tasks|tasks.md]] — 4 tasks: reproduce, fix backend, fix UI, verify regressions

---

## Steering Document Example: TaskFlow

A complete project steering document for a fictional SaaS task management application.

**Folder structure:**
```
Examples/taskflow-steering/
  CLAUDE.md            ← The steering document itself
```

**File:**
- [[Business Projects/Spec driven development/Examples/taskflow-steering/CLAUDE|CLAUDE.md]] — Project overview, tech stack, commands, project structure, code conventions, Always/Ask/Never boundaries

---

## How These Examples Map to Your Project

In a real project, the structure would look like:

```
your-project/
  CLAUDE.md                              ← Like taskflow-steering/CLAUDE.md
  specs/
    notification-preferences/            ← Like Examples/notification-preferences/
      brief.md
      requirements.md
      design.md
      tasks.md
    duplicate-order-emails/              ← Like Examples/duplicate-order-emails/
      bugfix.md
      tasks.md
```

The examples use the same filenames, structure, and conventions prescribed by the standard. Copy a folder, rename it, and replace the content.
