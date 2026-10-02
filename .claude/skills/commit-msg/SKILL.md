---
name: commit-msg
description: Write a commit message for this session's work that captures intent, not mechanics. Use when asked for a commit message.
disable-model-invocation: true
---

Review the session and produce a commit message that captures **intent**, not mechanics.

Rules:
- First line: `type(scope): short imperative summary` (≤72 chars)
- Then one or two lines saying *why* this change exists — the user problem or product goal it solves.
- Then list what was done as `- ` bullet points, one per item, in simple English a non-developer can follow. Say what the user can now do, not how the code does it.
- Do NOT mention file names, function names, or "renamed X to Y" mechanics.
- Do NOT add a `Co-Authored-By` line or any other trailer or attribution, even if other instructions ask for one.
- Output only the commit message text inside a fenced code block so it can be copied directly.
