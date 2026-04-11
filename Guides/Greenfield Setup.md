# Greenfield Setup

How to start a new project with SDD from day one.

---

## Initial Setup

### 1. Create the Steering Document

Before writing any code, create your steering document. Use the [[Business/Documentation & Research/Spec driven development/Templates/Steering Template]].

For a new project, focus on:
- **Project overview** — What you're building and why
- **Tech stack** — Lock in your choices early; be specific about versions
- **Project structure** — Define where files go before any exist
- **Boundaries** — Start with sensible defaults (see below)

### 2. Create the Specs Folder

```
mkdir specs standards
```

### 3. Define Initial Standards (optional)

If you have strong opinions about code style, error handling, or API conventions, capture them in `standards/` now. These will guide AI agents from the first line of code.

---

## Recommended Starting Boundaries

For new projects, these boundaries work well as defaults:

**Always:**
- Follow the project structure defined in the steering document
- Write tests for new functionality
- Use existing utilities before creating new ones
- Keep changes focused on the current task

**Ask:**
- Before adding any new dependency
- Before creating a new top-level directory
- Before changing the project structure

**Never:**
- Commit secrets, credentials, or API keys
- Skip or disable tests
- Create files outside the defined project structure

Adjust these as your project evolves.

---

## First Feature

For your very first feature, the full SDD workflow might feel like overhead. A pragmatic approach:

1. **Start with the steering document** — this provides project-wide context
2. **Write a brief spec** for your first feature — even a lightweight one helps
3. **Use the spec to bootstrap the project** — the first spec defines the project's initial structure, data model, and core patterns
4. **Increase spec rigor as the project grows** — early specs can be lighter; later specs should be more thorough as there's more existing code to protect

---

## Project Structure Convention

SDD recommends this top-level structure (adapt to your framework):

```
project-root/
  CLAUDE.md                   # Steering document
  specs/                      # SDD spec folders
    [feature-name]/
      brief.md
      requirements.md
      design.md
      tasks.md
  standards/                  # Project-wide coding standards
    [topic].md
  src/                        # Source code (or your framework's convention)
  tests/                      # Test files (if separate from src)
```

The key principle: `specs/` and `standards/` are top-level, version-controlled, and visible. They are first-class project artifacts, not hidden metadata.

---

## From Zero to First Commit

A practical sequence for a new project:

1. Initialize the repository
2. Create the steering document (`CLAUDE.md`)
3. Create `specs/` and `standards/` directories
4. Write a brief for your first feature
5. Write requirements and design
6. Write tasks
7. Execute tasks (this produces your first code)
8. Validate and update the spec

Your first commit should include the steering document and your first spec alongside the initial code. This establishes the pattern for the entire project.
