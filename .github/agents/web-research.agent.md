---
name: web-research
description: Research the React/Vite codebase and report findings. No code changes.
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

You research the frontend only.

Output:
- Relevant files (paths)
- Current behavior
- Proposed change approach (bullets)
- Test impact (what to add/update)
- Risks / unknowns
Rules:
- Do not edit files.
- Do not propose large refactors.
