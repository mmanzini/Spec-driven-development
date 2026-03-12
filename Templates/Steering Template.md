---
type: template
sdd-version: "0.1"
artifact: steering
---

# Steering Template

> [!info] Copy this template to your project root as `CLAUDE.md`, `.cursorrules`, `.github/copilot-instructions.md`, or whatever your AI tool uses. This is your project's constitution — it applies to all work in the project.

---

# [Project Name]

## Project Overview

[One paragraph describing what this project is, its purpose, and its current state.]

## Tech Stack

[Be specific — include versions where they matter.]

- **Language:** [e.g., TypeScript 5.4]
- **Framework:** [e.g., Next.js 14 with App Router]
- **Database:** [e.g., PostgreSQL 16 via Prisma ORM]
- **Testing:** [e.g., Vitest for unit tests, Playwright for e2e]
- **Other:** [e.g., Tailwind CSS, Redis for caching]

## Commands

```bash
# Build
[build command]

# Test
[test command]

# Lint
[lint command]

# Dev server
[dev command]
```

## Project Structure

```
[Key directories and their purpose — keep this high-level]
src/
  components/     # Shared UI components
  features/       # Feature-specific code, organized by feature
  lib/            # Shared utilities and helpers
  api/            # API routes
specs/            # SDD spec folders
standards/        # Project-wide coding standards
```

## Code Conventions

[Naming, formatting, patterns, and architectural rules.]

- [Convention 1: e.g., "Use camelCase for variables, PascalCase for components"]
- [Convention 2: e.g., "All API responses follow the { data, error, meta } shape"]
- [Convention 3: e.g., "Feature code lives in src/features/[feature-name]/"]

## Boundaries

### Always

- [e.g., "Run tests before completing any task"]
- [e.g., "Follow the existing file and folder structure"]
- [e.g., "Use the existing database schema"]

### Ask

- [e.g., "Before adding a new dependency"]
- [e.g., "Before changing a public API contract"]
- [e.g., "Before modifying shared configuration"]

### Never

- [e.g., "Never modify .env files or commit secrets"]
- [e.g., "Never push directly to main"]
- [e.g., "Never skip or disable tests"]
- [e.g., "Never modify CI/CD pipeline configuration"]

---

> [!tip] Delete all `> [!tip]` callouts and placeholder text when you're done. The steering document should contain only your project's actual conventions.
