# thoughts

Engineering notes and decisions for this repo.

This folder exists so decisions don’t live only in Slack, PR comments, or people’s heads.

## What belongs here
- Decisions and tradeoffs (why we chose approach A over B)
- Research findings that inform implementation
- Architecture notes and conventions (feature folders, patterns, boundaries)
- Risk notes (security, scalability, performance)
- “We tried X, it failed because Y”
- Follow-ups that should become backlog tickets

## What does NOT belong here
- Long specs that belong in `docs/`
- Backlog items (put those in `backlog/`)
- UX artifacts (put those in `ux/`)
- Meeting notes
- Raw logs or giant stack traces (summarize instead)

## Naming
Use: `YYYY-MM-DD-topic-slug.md`

Examples:
- `2026-02-01-auth-refresh-contract.md`
- `2026-02-01-pagination-strategy.md`

## Standard doc format
Every thoughts doc should include:

- Context
- Decision (or recommendation)
- Options considered
- Pros / cons
- Follow-ups (if any)
- Links (PRs, tickets, UX docs)

## Good hygiene
- Keep docs short. Prefer bullets.
- Prefer concrete file paths, symbols, and examples.
- If a doc becomes outdated, add a note at the top:
  - `Status: superseded by <new doc>`
- If a decision changes, write a new doc instead of rewriting history.
