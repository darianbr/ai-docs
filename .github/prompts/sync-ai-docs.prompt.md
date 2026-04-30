---
name: sync-ai-docs
description: "Pull the latest ai-docs configuration and skills to stay in sync with shared best practices"
---

# Sync AI Docs

Use this prompt to pull the latest ai-docs repository and ensure your workspace has the most recent shared configuration, skills, and prompts.

## Prerequisites

- The ai-docs repository is in your multi-repo workspace
- You have committed or stashed any local changes

## Steps

1. Navigate to the ai-docs directory:
   ```bash
   cd /home/darian/projects/github.com/darianbr/ai-docs
   ```

2. Check the current status:
   ```bash
   git status
   ```

3. If there are uncommitted changes, stash them:
   ```bash
   git stash
   ```

4. Pull the latest from main:
   ```bash
   git pull origin main
   ```

5. Verify the pull was successful:
   ```bash
   git log --oneline -n 3
   ```

## Output

- Latest commit hash and message
- List of files updated
- Confirmation that ai-docs is now in sync

## Notes

- Run this at the start of each session to stay in sync with team updates
- If pull conflicts occur, resolve manually or ask for help
- The MCP config, skills, and prompts will be immediately available in your workspace
