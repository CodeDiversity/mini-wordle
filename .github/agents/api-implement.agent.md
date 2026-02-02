---
name: api-implement
description: Implement backend changes in NestJS with tests, validation, security-first patterns, and scalable design (clean modules, predictable contracts, safe data access).
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

Implement the change in the NestJS API.

## Core rules
- Keep changes small and focused.
- Prefer clarity over cleverness.
- Don’t introduce new dependencies unless necessary.
- Optimize for maintainability and predictable behavior.

## Architecture (scalable NestJS)
- Keep controllers thin:
  - routing + auth/guards + DTO validation + mapping only
- Put business logic in services.
- Keep modules coherent:
  - feature modules own their controllers/services/DTOs
  - avoid cross-module imports that create cycles
- Prefer explicit boundaries:
  - controllers return response DTOs (not raw entities)
  - services accept well-typed inputs, return well-typed outputs

## DTOs and validation
- Use DTOs for all request inputs (body, params, query).
- Validate at the boundary using ValidationPipe (or existing repo approach).
- Enable/assume:
  - whitelist (strip unknown fields)
  - forbidNonWhitelisted when appropriate
  - transform for query/params types
- Never trust client-provided identifiers or roles.

## Security rules (required)
Treat every endpoint as hostile by default.

### AuthN/AuthZ
- Enforce authentication where required (guards).
- Enforce authorization explicitly:
  - verify the caller can access the resource (ownership/roles)
  - avoid “IDOR” (insecure direct object reference): never rely on a client-provided id alone
- Prefer policy-style checks (helper function/service) for reuse.

### Input and output safety
- Validate and sanitize inputs.
- Avoid returning sensitive fields (tokens, secrets, internal ids, PII) by default.
- Return consistent error shapes. Do not leak stack traces or internal messages.

### Data access safety
- Use parameterized queries / ORM safe methods only.
- Avoid dynamic SQL string building.
- Pagination for list endpoints (limit + cursor/offset). Enforce max limits.

### Rate limiting / abuse controls (if repo supports it)
- If a route is high-risk (login, search, expensive queries), apply throttling where available.
- If throttling isn’t present in the repo, document it as a follow-up ticket (don’t reinvent infra).

### Logging
- Log security-relevant events carefully:
  - log request ids, user ids, endpoint, status
  - never log credentials, tokens, secrets, or full payloads containing PII
- Prefer structured logs if the repo already supports them.

## Performance / scalability rules
- Avoid N+1 queries (batch or join where appropriate).
- Cache only if the repo already has a caching layer and it’s clearly beneficial.
- Keep operations idempotent where it matters (retries).
- Avoid long-running work in request/response:
  - if needed, queue/background job pattern (only if repo already has it)
  - otherwise document as follow-up

## Error handling
- Use built-in Nest exceptions (BadRequestException, NotFoundException, ForbiddenException, UnauthorizedException, ConflictException).
- Map domain errors to HTTP codes consistently.
- Don’t return 500 for expected client errors.

## Testing rules (Jest/Vitest depending on repo; default Nest is Jest)
- Update/add unit tests for services.
- Add e2e tests for controller routes if the repo has an e2e harness.
- Colocate tests next to files unless repo already uses a central folder:
  - `thing.service.ts` → `thing.service.spec.ts`
  - `thing.controller.ts` → `thing.controller.spec.ts`
- Add tests for:
  - authorization checks (forbidden when wrong user)
  - validation failures
  - happy path
  - edge cases (not found, conflict)

## Commands
- Run: `npm run lint`, `npm run typecheck`, `npm run test` (or closest equivalents).
- If monorepo, run commands in the correct package folder.

## Deliverable
Finish with:
- API behavior notes in the PR description:
  - new/changed endpoints
  - status codes
  - request/response example (short)
  - auth/role requirements
- Test commands run + results.
- Any security follow-ups as explicit bullets (only if needed).
