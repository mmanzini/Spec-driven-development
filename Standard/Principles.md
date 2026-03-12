# Principles

The core beliefs that drive Spec-Driven Development. These principles are not rules to follow mechanically — they are the reasoning behind every practice in the standard.

---

## 1. Specs Before Code

Time invested in specification reduces total implementation time. A clear spec eliminates ambiguity upfront, preventing costly rework. This is especially true with AI agents: a precise spec produces correct code on the first pass; a vague prompt produces code that needs multiple rounds of correction.

## 2. Feature-Scoped, Not Monolithic

One spec folder per feature or bugfix. Never a single giant specification document covering the entire project. Small, focused specs are easier to write, review, implement, and validate. They enable parallel work and clear ownership.

## 3. The Constitution Is Not a Spec

The [[Steering Template|steering document]] (e.g., `CLAUDE.md`) defines project identity — tech stack, conventions, boundaries. Feature specs define what to build. These are distinct concerns:

- **Steering document**: "We use TypeScript, follow these naming conventions, never modify production configs."
- **Feature spec**: "Build a password reset flow that sends an email with a time-limited token."

Conflating them leads to bloated context files that are neither good constitutions nor good specs.

## 4. Smarter Specs, Not Longer Specs

The "curse of instructions": as you add more instructions, adherence to each one drops. A 50-line spec with precise, testable requirements outperforms a 500-line spec full of vague guidance. Every sentence in a spec should earn its place.

## 5. Portable Across Tools

Specs are Markdown files. They work with Claude Code, Cursor, Copilot, Kiro, Windsurf, or any future tool that reads files. The standard never depends on a specific vendor's features. Tool-specific integration is an add-on, not a requirement.

## 6. Incremental Adoption

You don't need to adopt the full standard on day one. Start with a steering document. Add feature specs when complexity warrants it. Introduce the Product Brief when PO/PM collaboration becomes important. The standard is designed to be adopted in layers. See [[Adoption Guide]].

## 7. Living Documents

Specs can and should be updated during implementation. When building reveals something the design didn't anticipate, update the spec — don't silently diverge. The spec is the source of truth; if reality doesn't match the spec, one of them must change.

## 8. Human Decides, AI Executes

The human (PO/PM or Developer) owns every decision. The AI agent is a powerful executor, not an autonomous decision-maker. When the AI encounters ambiguity, the correct behavior is to flag it — not to guess.

## 9. Validate Against the Spec

Implementation is checked against the spec, not against intuition. Acceptance criteria from requirements become test cases. If it's not in the spec, it's not a requirement — and if it is in the spec, it must be verified.

## 10. Product Intent Drives Specs

The PO/PM owns the *why* and the *what*. Specs are the bridge between product vision and implementation. A well-written spec serves two audiences simultaneously: human developers who need context and rationale, and AI agents who need precision and explicit boundaries. See [[Roles]].
