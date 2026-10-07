---
name: git-commit-message
description: Suggest a Git commit message from the relevant staged or unstaged diff, using the user's Conventional Commit style.
---

# Git commit messages

When asked to suggest or refine a commit message:

1. Inspect the relevant diff. If changes are staged, base the message on the staged diff; otherwise use the unstaged diff. Do not infer the change from the prompt alone.
2. Write a concise Conventional Commit subject in imperative mood, without a final period. Keep it to 72 characters or fewer when practical.
3. Use `type(scope): subject` when the scope adds useful context. Common types include `feat`, `fix`, `docs`, `refactor`, `test`, `build`, `ci`, and `chore`. Use `!` for breaking changes.
4. Return the suggested message without committing.
