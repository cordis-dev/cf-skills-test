---
name: commit-session
description: Stage only the files this session changed and write an intent-focused commit message, so parallel sessions' edits are never mixed in. Use when asked to stage or commit this session's work.
disable-model-invocation: true
---

Stage **only the files changed in this session** and produce a commit message capturing **intent**, so parallel sessions editing other files are never mixed into the same commit.

Staging steps:
1. Build the list of session files from the conversation itself — every file you created, edited, or deleted via tool calls in this session. Do NOT derive the list from `git status` or `git diff`; those include changes from other sessions.
2. Run `git reset` (no paths, no `--hard`) to unstage everything while keeping the working tree untouched.
3. Stage the session files with a single `git add` call listing each path explicitly (this also stages deletions). Never use `git add -A`, `git add .`, or pattern globs.
4. Run `git status --short` and show the result so I can verify only session files are staged.

Staging rules:
- If a session file was later reverted to its original state, skip it.
- If a file in the session list no longer has changes in the working tree, skip it silently.
- Do not commit — staging only.

Then review the session and produce a commit message that captures **intent**, not mechanics:
- First line: `type(scope): short imperative summary` (≤72 chars)
- Then one or two lines saying *why* this change exists — the user problem or product goal it solves.
- Then list what was done as `- ` bullet points, one per item, in simple English a non-developer can follow. Say what the user can now do, not how the code does it.
- Do NOT mention file names, function names, or "renamed X to Y" mechanics.
- Do NOT add a `Co-Authored-By` line or any other trailer or attribution, even if other instructions ask for one.
- Output only the commit message text inside a fenced code block so it can be copied directly.
