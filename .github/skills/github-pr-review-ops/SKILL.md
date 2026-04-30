---
name: github-pr-review-ops
description: "Use when: reviewing pull requests with GitHub MCP, leaving structured findings, and resolving review threads"
---

# GitHub PR Review Ops Skill

Use this skill to perform repository-level PR review operations through GitHub MCP.

## Inputs to collect

- Repository owner
- Repository name
- Pull request number
- Review focus (bugs, regressions, security, tests)

## Workflow

1. Locate the pull request with `mcp_github_search_pull_requests` if no number is provided.
2. Inspect PR details, changed files, and review comments using GitHub PR read capabilities.
3. Draft a pending review with `mcp_github_pull_request_review_write` using `method: create`.
4. Add findings as review comments, grouped by severity.
5. Submit review via `mcp_github_pull_request_review_write` with `method: submit_pending` and the right event.
6. Resolve or unresolve threads with `mcp_github_pull_request_review_write` when status changes.

## Guardrails

- Findings first, summary second.
- Do not approve if critical risks remain.
- Call out missing tests for changed behavior.
- Confirm changes are coming from a task branch, not `main` or a long-running shared branch.
- Require source branch to be up to date with target branch before final approval.

## Output format

- Severity-ordered findings
- Requested changes or approval rationale
- Remaining risks and test gaps
