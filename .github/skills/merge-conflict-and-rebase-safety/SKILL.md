---
name: merge-conflict-and-rebase-safety
description: "Use when: resolving merge conflicts, rebasing branches, fast-forwarding merges, and ensuring clean history before merge"
---

# Merge Conflict and Rebase Safety Skill

Use this skill to safely resolve merge conflicts, rebase onto updated base branches, and maintain a clean, linear or organized commit history without accidental force pushes.

## Safety policy

- Resolve merge conflicts thoughtfully; do not keep conflicts unresolved.
- Rebase onto latest base branch to ensure all upstream changes are integrated.
- Never force-push without team awareness and coordination.
- Prefer linear history via rebase for feature branches; use merge commits for integration branches only.
- Document conflict resolutions and squash commits if needed for clarity.

## Inputs to collect

- Repository owner and name
- Source branch (feature) and target branch (base)
- Current merge conflict status

## Workflow

1. Detect if branch has merge conflicts or is behind base branch.
2. If behind, offer rebase or merge-base update with conflict preview.
3. For each conflict, inspect both versions and resolve intentionally.
4. Run tests after conflict resolution to catch integration failures.
5. Confirm rebased commit history is clean and linear (no unnecessary merge commits).
6. Verify no unintended commits were introduced during rebase.
7. Require explicit confirmation before force-pushing rebased commits.

## Guardrails

- Do not push unresolved merge conflicts.
- Do not force-push without team coordination; require explicit approval.
- Block force-push on `main` and long-running shared branches; only allow on feature branches with owner acknowledgment.
- Verify tests pass after conflict resolution.
- Ensure rebase does not duplicate or lose commits.

## Output format

- Merge conflict detection and summary
- Conflict resolution strategy and results
- Rebase plan and impact on commit history
- Test results post-conflict-resolution
- Force-push confirmation checkpoint
