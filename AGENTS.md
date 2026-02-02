# AGENTS.md

## Tech
- Frontend: React + Vite + TypeScript, Redux Toolkit + Styled Components
- Frontend tests: Vitest
- Frontend lint: ESLint
- Backend: NestJS + TypeScript
- Prefer small PRs with clear scope.

## Default workflow
- Clarify the goal in the PR description with acceptance criteria.
- Make the smallest change that meets the acceptance criteria.
- Add or update tests for behavior changes.
- Run checks before finishing and report results in the PR.

## Commands (frontend)
- Install: npm ci
- Dev: npm run dev
- Test: npm run test
- Lint: npm run lint
- Typecheck: npm run typecheck

## Commands (backend)
- Dev: npm run start:dev
- Test: npm run test
- Test (watch): npm run test:watch
- Lint: npm run lint
- Typecheck: npm run typecheck

## Code style rules
- Prefer explicit types at module boundaries (API payloads, DTOs, public functions).
- Avoid large refactors unless required.
- Prefer composition over clever abstractions.

## NestJS rules
- Validate inputs using DTOs + validation pipe where applicable.
- Keep controllers thin: validation + routing only.
- Put business logic in services.
- Use clear error responses (HTTP exceptions) and consistent status codes.

## Frontend rules
- Keep components small.
- Put async logic in hooks/services, not in JSX.
- Prefer Testing Library style tests over implementation-detail tests.

## Backlog grooming cadence
- Weekly grooming: archive done items, merge duplicates, split L items, re-evaluate priorities.
- Keep “Now” limited to 3–7 ready tickets.
