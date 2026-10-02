---
name: diff-review
description: Run /code-review scoped to currently changed files.
disable-model-invocation: true
allowed-tools: Bash(git status *)
---

Changed files:

!`git status --porcelain -uall | grep -vE '^(D|.D)' | cut -c4- | sed 's/.* -> //'`

Run `/code-review` with exactly those paths as the argument. Nothing else.
