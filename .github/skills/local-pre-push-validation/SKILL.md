---
name: local-pre-push-validation
description: "Use when: before pushing commits to a branch, validate local build, tests, linting, and commit message quality to prevent broken builds"
---

# Local Pre-Push Validation Skill

Use this skill to run essential checks before pushing to remote to catch issues early and avoid polluting the upstream repository.

## Safety policy

- Run tests locally and confirm they pass before push.
- Run linting and type checks; do not push code with style or type violations.
- Confirm commit messages are descriptive and follow conventions.
- Validate that no large binaries, secrets, or environment-specific configs are staged.
- Summarize what will be pushed and pause for confirmation.

## Inputs to collect

- Repository owner and name
- Files staged for commit
- Commit message(s)
- Local test and lint command(s)

## Workflow

1. Verify staged files are intentional (no accidental `.env`, `.local`, `node_modules`, etc.).
2. Run local lint and type checks; block commit if violations exist.
3. Run local test suite; block push if tests fail or coverage drops.
4. Review commit message(s); ensure they are descriptive and tied to a task/issue number.
5. Summarize the change scope and seek confirmation before push.
6. Execute push only after all checks pass and user confirms.

## Guardrails

- Block push if any test, lint, or type check fails.
- Reject vague commit messages (e.g., "fix", "update", "changes").
- Warn if commit touches unrelated file categories.
- Warn if commit is unusually large (e.g., > 500 lines).
- Block push if secrets or sensitive files are detected in package contents.

## Output format

- Local validation results (tests, lint, types)
- File scope summary
- Commit message review
- Final confirmation checkpoint
