---
name: structured-reasoning
description: >
  Structured reasoning framework for coding tasks. Use this skill for any coding task:
  bug fixing, code review, writing new code, debugging intermittent issues, or refactoring.
  Enforces explicit exploration and planning before any implementation, and structured
  reasoning before every tool call throughout the agentic loop.
---

# Structured Reasoning Framework

Two rules govern every response:

1. **Run a full reasoning protocol before your first action.** Choose the protocol from the table below and complete every section before touching any code or tool.
2. **Wrap every tool call with a pre-action and post-observation block.** This applies to every tool call for the rest of the session — not just the first one.

---

## Full Protocol (run once, at the start)

Choose the protocol that matches the task and read it from `references/protocols.md`.

| Task | Protocol |
|------|----------|
| Fix a reported bug | `bug-fix` |
| Find issues in existing code | `code-review` |
| Write new code from a description | `code-generation` |
| Diagnose an unclear or intermittent issue | `deep-debug` |
| Restructure code without changing behavior | `refactor` |

### Exploration rules (apply to all protocols)

These rules govern how you write inside every section:

- **Scratchpad first.** Every protocol begins with an unstructured `<scratchpad>` block. Write everything you notice, suspect, or are uncertain about — including wrong ideas. Messy is correct. This is not a section to summarize — it is where you think before you structure.
- **Enumerate before committing.** Any section that asks for a cause, plan, or solution requires at least 3 candidates listed before you converge on one. Picking the first plausible idea without considering alternatives is not allowed.
- **Stay hedged until `<implementation>`.** In every section before implementation, use uncertain language: "I think," "one possibility is," "this might be because." Definitive statements belong only in `<implementation>`.
- **Revise out loud.** If you change your mind mid-section, do not delete. Write "Wait —" or "Actually," and continue with the correction. Sections should show the working, not a cleaned-up final answer.
- **Red-team before moving on.** Before transitioning to the next section, answer: *"What would have to be true for my current conclusion to be wrong?"* If you can answer it, address it before continuing.

---

## Per-Action Loop (run before and after every tool call)

Before every tool call — editing a file, running tests, reading a file, running a command — write a `<pre_action>` block. After the result comes back, write a `<post_observation>` block. No exceptions.

### `<pre_action>`
```
What I'm about to do: [specific action]
Why this action, right now: [reasoning — not just "run tests" but why these tests, why now]
What I expect to see: [concrete prediction]
If I see something different: [what that would mean and what I'd do]
```

### `<post_observation>`
```
What I actually saw: [result — be specific, reference actual output]
Expected vs. actual: [where did my prediction match or diverge]
What this tells me: [updated understanding of the problem]
Does this change my plan: [yes/no — if yes, state the new direction before acting again]
```

The `<post_observation>` from one action feeds directly into the `<pre_action>` of the next. If a test fails, the post-observation must articulate *why* it failed and *what specifically* you will change before you write the next pre-action. Jumping from a failed test to an edit without this block is not allowed.
