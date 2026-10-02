---
name: diff-polish
description: Run /simplify then /code-review, both scoped to currently changed files.
disable-model-invocation: true
allowed-tools: Bash(git status *)
---

Changed files:

!`git status --porcelain -uall | grep -vE '^(D|.D)' | cut -c4- | sed 's/.* -> //'`

1. Run `/simplify` with exactly those paths as the argument.
2. Run `git status --porcelain -uall` again, drop deleted files, and run `/code-review` with the resulting paths as the argument.
3. After `/code-review` finishes, write one final message: first the `/simplify` final response, then the `/code-review` final response.
