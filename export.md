---
name: export
description: Export prior implementation discussions into a polished HTML agent document. Use only when the user explicitly invokes this skill by name, such as "/export", "use the export skill", or "run export"; do not use for ordinary requests to summarize, document, explain, or implement code unless the user explicitly names the export skill.
---

# Export

## Overview

Create an HTML implementation brief from the current or previous conversation about planned codebase behavior. The output is a standalone tech-docs style page in `agent-docs/` under the current working directory.

## Workflow

1. Gather the relevant conversation context before writing. Focus on decisions, intended behavior, constraints, implementation choices, codebase impact, and unresolved questions.
2. Inspect the active repository only as needed to accurately reference files, folders, architecture, or examples discussed in the conversation.
3. Create `agent-docs/` in the current directory if it does not exist.
4. Write one new `.html` file in `agent-docs/`. Use a descriptive, hyphenated filename based on the topic, such as `agent-docs/auth-flow-implementation.html`.
5. Make the document useful to a future coding agent or engineer implementing the discussed changes.
6. Verify the file exists and briefly report the path.

## Required Output

The exported HTML must include:

- A clear title and short summary of the planned implementation.
- A decision log describing the behaviors, rules, and tradeoffs agreed in the conversation.
- Expected user-facing and developer-facing behavior.
- Impact summary listing changed or added files, folders, modules, APIs, routes, commands, config, tests, or data structures when known.
- Expected architecture changes, including ownership boundaries and integration points.
- Short, focused code examples only when they clarify a core decision or expected behavior.
- Constraints, assumptions, non-goals, and open questions.
- Implementation checklist ordered in a practical sequence.

If some details were not discussed, include a concise "Unknowns" or "Open Questions" section rather than inventing specifics.

## HTML Style

Produce a complete standalone HTML document with embedded CSS. The page should read like a modern technical documentation site:

- Use semantic sections, a readable content width, sticky or clearly visible navigation when useful, and strong typographic hierarchy.
- Prefer neutral, professional styling with high contrast and good spacing.
- Use tables for file-impact summaries when they improve scanability.
- Use callouts for important decisions, risks, assumptions, and open questions.
- Use syntax-highlight-like styling for code blocks without depending on external scripts or CDNs.
- Do not require network access, external fonts, or remote assets.

## Content Rules

- Document what was discussed and decided; do not turn the export into a new implementation plan that contradicts the conversation.
- Separate confirmed decisions from inferred recommendations.
- Keep code examples short and directly tied to a decision or expected behavior.
- Do not include large source listings, generated boilerplate, or unrelated repository details.
- Use concrete file paths and component/module names when known.
- Make the document actionable enough that another agent can continue implementation from it.

## File Naming

Use lowercase hyphenated filenames ending in `.html`. If the conversation does not have a specific topic, use `agent-docs/implementation-decisions.html`. If that file already exists, append a short timestamp or topic suffix instead of overwriting unless the user explicitly asks to replace it.

## Validation

Before finishing, inspect the generated HTML for obvious structural problems. When practical, confirm it contains the expected major sections and no placeholder text.
