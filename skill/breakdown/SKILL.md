---
name: breakdown
description: >
  Problem breakdown framework for coding tasks. Use this skill for any coding task:
  bug fixing, code review, writing new code, debugging intermittent issues, or refactoring.
  Requires a thorough written analysis using structured sections before any code or action.
---

# Breakdown

## Requirement

Every coding response begins with a written breakdown using the sections defined in
`references/protocols.md`. Choose the protocol that matches the task and complete every
section before writing code or taking any action. Do not skip sections. Do not abbreviate.
A short breakdown is an incomplete response.

## Protocol Selection

| Task                                       | Protocol          |
| ------------------------------------------ | ----------------- |
| Fix a reported bug                         | `bug-fix`         |
| Find issues in existing code               | `code-review`     |
| Write new code from a description          | `code-generation` |
| Diagnose an unclear or intermittent issue  | `deep-debug`      |
| Restructure code without changing behavior | `refactor`        |

## Decision Gate — Required Before Every Action

Before taking any action — editing a file, running a command, calling a tool, writing
code — you must answer all three of the following. No action is exempt, including actions
that seem obvious.

**1. What are all the options?**
List every reasonable course of action available at this moment. Do not proceed with one
option before you have genuinely considered the others. An action taken without enumerating
alternatives is a reckless action.

**2. Why is this option definitively the best?**
Argue for the chosen action and against every alternative. Not "this seems right" — state
specifically why each alternative is inferior or ruled out. If you cannot make that case
with certainty, you are not ready to act. Keep working until you can.

**3. What is the strongest argument against this action?**
State the best case against your chosen action. Then answer it. If you cannot answer it,
do not proceed — revise your choice or gather more information first. An unresolved
objection is a reason to stop, not a reason to continue carefully.

These three questions are not a formality. If the answers are thin, the action is not
justified. There is no urgency that overrides this gate. No action is so small or so
obvious that it bypasses the requirement to justify it.

## Rules That Apply to Every Protocol

**Scratchpad first.** Every protocol begins with a `<scratchpad>`. Write everything you
notice, suspect, or are uncertain about — including wrong ideas. Do not move on until you
have exhausted your first-pass observations. This is not a section to summarize — it is
where you work before you structure.

**Enumerate before committing.** Any section that asks for a cause, plan, or solution
requires multiple candidates before converging. Pick the first plausible idea and you
will frequently pick the wrong one.

**Steelman before dismissing.** When arguing against a candidate, make the strongest case
for it first. Dismissing a weak version of an idea is not the same as ruling it out.

**Stay hedged until `<implementation>`.** Use uncertain language — "I think," "one
possibility," "this might be" — in every section before implementation. Confident
statements belong only in `<implementation>`.

**Revise out loud.** If your assessment changes mid-section, write "wait" or "actually"
and continue. Do not delete — the revision is part of the analysis.

**Red-team before each transition.** Before moving to the next section, answer: what
would have to be true for my current conclusion to be wrong? If the answer surfaces
something unaddressed, handle it before continuing.

**After any result, update before acting.** When a test fails or something unexpected
comes back, return to the relevant protocol section and update the analysis before
taking the next action. Do not move from a failed result directly to a new action.
