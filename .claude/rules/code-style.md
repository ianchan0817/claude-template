---
description: Code style and formatting conventions — always active across all engineers
---

# Code Style

## General
- 2-space indentation
- Single quotes for strings
- No trailing semicolons (unless the language requires them)
- Max line length: 100 characters
- Trailing newline at end of every file
- No trailing whitespace

## Naming
- `camelCase` for variables and functions
- `PascalCase` for classes, types, interfaces, components
- `SCREAMING_SNAKE_CASE` for constants
- `kebab-case` for file names and CSS classes
- Names are descriptive — no abbreviations unless universally understood (`id`, `url`, `api`)
- Boolean variables prefixed: `is`, `has`, `can`, `should` (e.g., `isLoading`, `hasError`)

## TypeScript
- No `any` — use `unknown` and narrow, or define the type
- Explicit return types on all public functions
- Prefer `interface` for object shapes, `type` for unions and intersections
- No `!` non-null assertion without a comment explaining why it's safe
- Strict mode on (`"strict": true` in tsconfig)

## Functions
- One responsibility per function
- Max 30 lines — if longer, extract
- No side effects in pure functions
- Early returns over nested conditionals

## Comments
- Comment the *why*, not the *what*
- No commented-out code in commits
- `// TODO(name): description` format for tracked todos — link to an issue

## Imports
- Absolute imports over relative where the framework supports it
- Group: external packages → internal modules → local files
- No unused imports (enforced by linter)
