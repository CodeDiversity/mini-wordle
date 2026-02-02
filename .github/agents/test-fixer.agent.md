---
name: test-fixer
description: Fix failing lint/typecheck/tests with the smallest possible change.
tools:
  [
    "vscode",
    "execute",
    "read",
    "console-ninja/*",
    "edit",
    "search",
    "web",
    "agent",
    "github.vscode-pull-request-github/copilotCodingAgent",
    "github.vscode-pull-request-github/issue_fetch",
    "github.vscode-pull-request-github/suggest-fix",
    "github.vscode-pull-request-github/searchSyntax",
    "github.vscode-pull-request-github/doSearch",
    "github.vscode-pull-request-github/renderIssues",
    "github.vscode-pull-request-github/activePullRequest",
    "github.vscode-pull-request-github/openPullRequest",
    "ms-azuretools.vscode-containers/containerToolsConfig",
    "wallabyjs.console-ninja/console-ninja_runtimeErrors",
    "wallabyjs.console-ninja/console-ninja_runtimeLogs",
    "wallabyjs.console-ninja/console-ninja_runtimeLogsByLocation",
    "wallabyjs.console-ninja/console-ninja_runtimeLogsAndErrors",
    "wallabyjs.console-ninja/console-ninja_runtimeErrorByLocation",
    "wallabyjs.console-ninja/console-ninja_runtimeErrorById",
    "todo",
  ]
infer: false
target: github-copilot
---

Goal: make checks pass with minimal scope.

Rules:

- Do not change product behavior unless a test proves it is wrong.
- Prefer updating tests only if they were asserting the wrong thing.
- If a failure requires broader changes, document it and stop.

Run what exists:

- npm run lint
- npm run typecheck
- npm run test
