# copilot-agents

A small repository of team conventions, artifacts, and workflows for the Copilot Agents project. It centralizes backlog tickets, planning notes, UX artifacts, and contributor guidance used by engineers working on frontend and backend pieces.

## Table of contents

- Quickstart
- Repository structure
- Development workflow & expectations
- Tech stack
- Code style & engineering rules
- Backlog grooming cadence
- How to contribute
- More docs & contacts
- License & next steps

## Quickstart

Prerequisites

- Git
- Node.js (LTS) and npm

Clone

```bash
git clone <repo-url>
cd copilot-agents
```

Install (root or package-specific as applicable)

```bash
npm ci
```

Common commands

Frontend (run from the frontend package or repo root if commands are top-level)

```bash
# install dependencies
npm ci

# dev
npm run dev

# tests
npm run test

# lint
npm run lint

# typecheck
npm run typecheck
```

Backend (run from the backend package or repo root if commands are top-level)

```bash
# dev server
npm run start:dev

# tests
npm run test

# tests (watch)
npm run test:watch

# lint
npm run lint

# typecheck
npm run typecheck
```

Run the relevant commands from the package root that contains the frontend or backend code when the repository is split into packages.

## Repository structure

- `backlog/` — backlog tickets and templates (see `backlog/tickets/_TEMPLATE.md`)
- `plans/` — planning documents and roadmaps
- `thoughts/` — working notes, decisions, and constraints
- `ux/` — user-experience artifacts (wireframes, flows, research)
- `AGENTS.md` — authoritative source for tech stack, commands, and workflows

## Development workflow & expectations

- Clarify the goal in the PR description with clear acceptance criteria.
- Make the smallest change that meets the acceptance criteria.
- Add or update tests for behavior changes.
- Run checks (tests, lint, typecheck) before finishing and report results in the PR.
- Prefer small PRs with clear scope.

## Tech stack

- Frontend: React + Vite + TypeScript, Redux Toolkit + Styled Components
- Frontend tests: Vitest
- Frontend lint: ESLint
- Backend: NestJS + TypeScript

## Code style & engineering rules

General

- Prefer explicit types at module boundaries (API payloads, DTOs, public functions).
- Avoid large refactors unless required.
- Prefer composition over clever abstractions.

NestJS (backend) rules

- Validate inputs using DTOs + validation pipe where applicable.
- Keep controllers thin: validation + routing only.
- Put business logic in services.
- Use clear error responses (HTTP exceptions) and consistent status codes.

Frontend rules

- Keep components small.
- Put async logic in hooks/services, not in JSX.
- Prefer Testing Library style tests over implementation-detail tests.

## How to contribute

- Open an issue or create a ticket using the template at `backlog/tickets/_TEMPLATE.md`.
- For changes, open a PR with:
  - A short description and clear acceptance criteria
  - The minimal change required to meet those criteria
  - Tests for changed behavior
  - Results of lint/typecheck/tests in the PR description
- Keep PRs small and focused.

## More documentation & contacts

Primary reference: `AGENTS.md`

Other artifact folders:

- `backlog/`
- `plans/`
- `thoughts/`
- `ux/`

Check those folders for tickets, plans, and UX artifacts. Reach out to repository maintainers via your team channels for questions or handoffs.
