# Getting Started

Adopt SDD in 5 minutes. This guide gives you the minimal viable setup — you can add more structure later as your project grows.

---

## Step 1: Create Your Steering Document (2 minutes)

Copy the [[Business/Documentation & Research/Spec driven development/Templates/Steering Template]] to your project root. Name it based on your AI tool:

| Tool | Filename |
|------|----------|
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursorrules` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Multiple tools | `CLAUDE.md` (most tools can read any named file) |

Fill in the essentials:
- Project overview (1 sentence)
- Tech stack (be specific)
- Key commands (build, test, lint)
- 2-3 boundaries per category (Always/Ask/Never)

You can skip the full Project Structure and Code Conventions sections for now — add them when you feel the need.

## Step 2: Create Your Specs Folder (30 seconds)

```
mkdir specs
```

That's it. The folder is empty until you need your first spec.

## Step 3: Write Your First Spec (when ready)

When you have a feature that's complex enough to benefit from planning:

1. Create a folder: `specs/[feature-name]/`
2. **(PO/PM)** Write a `brief.md` using the [[Business/Documentation & Research/Spec driven development/Templates/Product Brief Template]] — or skip this and go directly to requirements
3. **(PO/PM + Dev)** Write `requirements.md` using the [[Business/Documentation & Research/Spec driven development/Templates/Feature Spec Template]]
4. **(Dev)** Write `design.md`
5. **(Dev)** Write `tasks.md`
6. **(AI + Dev)** Execute tasks
7. **(PO/PM + Dev)** Validate against requirements

---

## What You Can Skip

SDD is designed for incremental adoption. Here's what's optional:

| Component | When to add it |
|-----------|---------------|
| `brief.md` | When PO/PM and Dev are different people, or when product context matters |
| `standards/` folder | When you have conventions that apply across multiple features |
| `research.md` | When you explored alternatives worth documenting |
| Full EARS notation | When requirements need to be very precise (complex systems, compliance) |

---

## Next Steps

- [[Business/Documentation & Research/Spec driven development/Guides/PO Guide to SDD]] — If you're a Product Owner or Product Manager
- [[Business/Documentation & Research/Spec driven development/Guides/Writing Requirements]] — How to write requirements in different notations
- [[Business/Documentation & Research/Spec driven development/Guides/Brownfield Adoption]] — If you're adding SDD to an existing codebase
- [[Business/Documentation & Research/Spec driven development/Guides/Greenfield Setup]] — If you're starting a new project from scratch
- [[Business/Documentation & Research/Spec driven development/Standard/Adoption Guide]] — The full incremental adoption path
