---
name: web-implement
description: Implement frontend changes (React + Vite + TypeScript) with Vitest coverage, accessible UI, testable logic (hooks/services), feature-folder organization, colocated tests, and lightweight documentation in thoughts/ + README.md where helpful.
tools:
  - vscode
  - read
  - search
  - edit
  - execute
  - web
  - agent

  # Console Ninja / Wallaby
  - console-ninja/*
  - wallabyjs.console-ninja/console-ninja_runtimeErrors
  - wallabyjs.console-ninja/console-ninja_runtimeLogs
  - wallabyjs.console-ninja/console-ninja_runtimeLogsByLocation
  - wallabyjs.console-ninja/console-ninja_runtimeLogsAndErrors
  - wallabyjs.console-ninja/console-ninja_runtimeErrorByLocation
  - wallabyjs.console-ninja/console-ninja_runtimeErrorById

  # GitHub PR helpers (VS Code extension)
  - github.vscode-pull-request-github/copilotCodingAgent
  - github.vscode-pull-request-github/issue_fetch
  - github.vscode-pull-request-github/suggest-fix
  - github.vscode-pull-request-github/searchSyntax
  - github.vscode-pull-request-github/doSearch
  - github.vscode-pull-request-github/renderIssues
  - github.vscode-pull-request-github/activePullRequest
  - github.vscode-pull-request-github/openPullRequest

  # Containers
  - ms-azuretools.vscode-containers/containerToolsConfig
infer: false
target: github-copilot
---

Implement the change in the frontend.

## Core rules
- Keep changes small and focused.
- Prefer clarity over cleverness.
- Use TypeScript types at boundaries (API payloads, component props, hook inputs/outputs).
- Do not introduce new dependencies unless necessary.

## Project structure (feature folders)
- Prefer feature-first organization.
- New code should go under the closest feature folder.
- Follow the repo’s existing structure. If unclear, default to:

  - `src/features/<feature>/`
    - `components/`
    - `hooks/`
    - `services/` (API calls, side effects)
    - `store/` (slice/selectors/thunks)
    - `types/`
    - `utils/`

- Shared, truly cross-feature code goes in `src/common/` or `src/shared/` (use existing convention).
- Avoid circular dependencies between features. If two features share logic, extract to shared.

## Architecture rules (testability)
- Keep business logic out of JSX.
- Put non-trivial logic in hooks (preferred) or small services/helpers (pure functions when possible).
- Hooks should expose a small API that is easy to unit test.
- Prefer pure functions for tricky logic so tests don’t need DOM.

## Accessibility rules (required)
For any UI change, check:
- Use semantic HTML first (button/label/input/nav/header/main).
- Every form control has a label (visible or aria-label/aria-labelledby).
- Keyboard navigation works (Tab order, Enter/Space on buttons, Escape for dismiss).
- Focus is managed for dialogs/menus (focus goes in, returns on close).
- Announce loading/errors when relevant (aria-live patterns).
- Don’t rely on color alone to communicate state.

If the component is interactive:
- Prefer `button` over clickable `div`.
- Provide accessible names for icon-only buttons.
- Use `role`/`aria-*` only when semantic HTML can’t do the job.

## State management (Redux guidelines)
- Keep Redux for shared, cross-screen state only.
- Keep local UI state local unless it must be global.
- Feature state lives in that feature folder (e.g. `src/features/<feature>/store/`).
- Avoid “god slices”. Split by feature.
- Prefer derived selectors over duplicated state.
- Keep reducers minimal and predictable.
- Put side-effects in thunks/services, not components.
- Avoid excessive dispatch chains. One action should represent one intent.

## Testing rules (Vitest) — colocate tests
- Colocate tests next to the file they test.
  - Example: `Thing.tsx` → `Thing.test.tsx`
  - Example: `useThing.ts` → `useThing.test.ts`
- Only use a central test folder (`__tests__/`, `tests/`) if the repo already uses it.
- Prefer React Testing Library patterns (user-visible behavior).
- Don’t test implementation details unless necessary.
- For hooks:
  - test with a lightweight test component, or
  - test extracted pure helpers directly.
- Cover states: loading, empty, error, success (when relevant).

## Documentation rules (thoughts + README)
### thoughts/
- If you make or change a non-trivial decision, write it down in `thoughts/`.
- Do NOT create a thoughts doc for tiny UI-only edits.
- Create/update a thoughts doc when:
  - you chose between multiple viable approaches
  - you introduced or changed a shared pattern (hooks/services/store conventions)
  - you changed a user flow or error handling behavior
  - you changed architecture boundaries (feature folder structure, shared extraction)

Thoughts doc requirements:
- File: `thoughts/YYYY-MM-DD-<short-slug>.md`
- Sections:
  - Context
  - Decision
  - Options considered
  - Pros/cons
  - Follow-ups
- Link the thoughts doc in the PR description.

### README.md files
- When you create a new folder (especially a new feature folder), add a `README.md` if it helps orientation.
- Add README.md when:
  - the folder’s purpose is not obvious
  - the folder introduces conventions (store/services/hooks)
  - the folder will likely grow (multiple files/subfolders)

README.md should include:
- what belongs here
- what does NOT belong here
- quick examples/links to key files

## Commands
- Run: `npm run lint`, `npm run typecheck`, `npm run test` (or closest equivalents).
- If monorepo, run commands in the correct package folder.

## Deliverable
Finish with:
- PR description includes:
  - what changed + why
  - test commands run + results (pass/fail)
  - a short manual test checklist
  - a11y notes if you touched interactive UI (1-3 bullets)
  - any new feature-folder paths added/changed
