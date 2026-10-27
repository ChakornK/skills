---
name: structured-reasoning
description: >
  Structured reasoning framework for coding tasks. Use this skill for any coding task:
  bug fixing, code review, writing new code, debugging intermittent issues, or refactoring.
  Enforces explicit analysis and planning before any implementation.
---

# Structured Reasoning Framework

Before responding to any coding task, complete all required reasoning sections in order.
Do not write code until all pre-implementation sections are finished.

## Core Loop

```
[ANALYSIS]   → Observe and inventory. No conclusions yet.
[ROOT CAUSE] → Trace exactly why the problem exists.
[PLAN]       → Decide what to change and why, in plain English.
[IMPL]       → Write the code.
[VERIFY]     → Confirm the fix addresses the root cause.
```

## Task Protocols

Choose the protocol that matches the task. Full protocols are in `references/protocols.md`.

| Task | Protocol |
|------|----------|
| Fix a reported bug | `bug-fix` |
| Find issues in existing code | `code-review` |
| Write new code from a description | `code-generation` |
| Diagnose an unclear or intermittent issue | `deep-debug` |
| Restructure code without changing behavior | `refactor` |

Read `references/protocols.md` and follow the matching protocol exactly.
