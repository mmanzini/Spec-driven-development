# Tool Agnosticism

SDD is designed to work with any AI coding tool. Specs are Markdown files — any tool that reads files can use them.

---

## Core Principle

The SDD standard never depends on a specific vendor's features. Tool-specific integration is an add-on, not a requirement. If your AI tool disappears tomorrow, your specs remain valuable as documentation and can be used with any replacement.

---

## How SDD Maps to Popular Tools

### Claude Code

| SDD Concept | Claude Code Equivalent |
|-------------|----------------------|
| Steering document | `CLAUDE.md` at project root |
| Spec context | Read spec files directly or reference via conversation |
| Boundaries | Defined in `CLAUDE.md` and respected by Claude |
| Task execution | Claude reads `tasks.md` and executes sequentially |

### Cursor

| SDD Concept | Cursor Equivalent |
|-------------|-------------------|
| Steering document | `.cursorrules` at project root |
| Spec context | Reference spec files in chat or as context |
| Standards | Can be included as rules or referenced files |
| Task execution | Use Composer with spec context |

### GitHub Copilot

| SDD Concept | Copilot Equivalent |
|-------------|-------------------|
| Steering document | `.github/copilot-instructions.md` |
| Spec context | Reference spec files in Copilot Chat |
| Standards | Include in instructions file or reference separately |

### Kiro

| SDD Concept | Kiro Equivalent |
|-------------|----------------|
| Steering document | Project-level context |
| Spec folder | `.kiro/specs/[feature]/` (Kiro's native format) |
| Requirements | `requirements.md` (matches Kiro's native format) |
| Design | `design.md` (matches Kiro's native format) |
| Tasks | `tasks.md` (matches Kiro's native format) |

SDD's spec structure is intentionally compatible with Kiro's format. Migration between SDD and Kiro is trivial.

### Other Tools

Any AI tool that can read files from the project directory can use SDD specs. The minimum requirement is:
1. The tool can read the steering document for project context
2. The tool can read spec files when given a file path
3. The tool follows instructions written in Markdown

---

## The Steering Document Bridge

The steering document is the only file with a tool-specific name. Everything else is standard Markdown in standard directories.

If you use multiple tools on the same project:
- Use `CLAUDE.md` as the primary (most tools can read any named file)
- Symlink or copy for tools that require a specific filename
- Or maintain parallel files with the same content (less ideal, but works)

The content structure remains identical regardless of filename. See [[Steering Template]].

---

## Portable Spec References

When referencing specs in conversations with AI tools:

```
Read the spec at specs/password-reset/requirements.md and implement task 3
from specs/password-reset/tasks.md
```

This works identically across all tools. The spec is the context — the tool is just the execution environment.
