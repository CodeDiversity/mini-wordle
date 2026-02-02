# plans

Implementation plans that turn research + UX + decisions into buildable steps.

This folder is for “how we will build it” documents. Keep them practical and scoped to shippable slices.

## What belongs here
- Step-by-step implementation plans for features/changes
- Sequencing and dependencies (web vs api order)
- Acceptance criteria and test plans
- Rollout and rollback notes
- Links to related `thoughts/`, `ux/`, and `backlog/` artifacts

## What does NOT belong here
- Product strategy or long-term vision docs
- Backlog tickets (those go in `backlog/`)
- Decision logs (those go in `thoughts/`)
- Pixel-perfect designs (those go in `ux/` or Figma)

## Naming
Use: `YYYY-MM-DD-topic-slug.md`

Examples:
- `2026-02-01-auth-refresh-plan.md`
- `2026-02-01-user-search-plan.md`

## Standard plan format
Each plan should include:

- Goal
- Non-goals
- Current behavior (with file paths)
- Proposed behavior
- Plan (numbered steps)
- Acceptance criteria
- Test plan
  - Web: Vitest + RTL
  - API: unit/e2e (depending on repo)
- Rollout plan
- Rollback plan
- Open questions / assumptions
- Links (thoughts, UX docs, tickets)

## Good hygiene
- Keep plans small and sliceable. Prefer the first shippable increment.
- If the plan grows too large, split it into multiple plans and link them.
- When work ships, add a note at the top:
  - `Status: implemented in PR <link or ref>`
