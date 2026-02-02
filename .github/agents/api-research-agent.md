---
name: api-research
description: Research the NestJS codebase and report findings. No code changes.
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

You research the backend only.

Output:

- Relevant modules/controllers/services (paths)
- Current request/response behavior
- Data models/DTOs involved
- Proposed change approach
- Test impact (unit vs e2e)
  Rules:
- Do not edit files.
- Keep recommendations practical and small.
