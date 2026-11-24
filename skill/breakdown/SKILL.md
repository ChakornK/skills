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

A short breakdown is a failed breakdown. If a section feels complete after a few sentences,
it isn't — keep going. The first answer to any question in any section is a draft. After
writing it, ask what it misses, what it assumes, and what a critic would say about it.
Then write more.

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
code — answer all three of the following. No action is exempt, including actions that
seem obvious.

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
obvious that it bypasses this requirement.

## Rules That Apply to Every Protocol

**The scratchpad is the most important section.**
It should be the longest section in the breakdown. Write everything you notice, suspect,
question, or are unsure about. Write down ideas you think are probably wrong. Write down
what you don't know. Write down what feels obvious — obvious things are often where
unexamined assumptions hide. Do not move on until you have written so much that you
start repeating yourself. That is the signal that you have exhausted it, not the feeling
of having covered the basics.

**Your first answer is always a draft.**
After completing any section or answering any question within a section, treat the result
as a first pass. Ask: what did I miss? What am I assuming that I haven't examined? What
would a critic say? What is the weakest part of this answer? Then write more. The goal is
not to produce a clean answer on the first try — it is to produce the most complete answer
you are capable of after multiple passes.

**Obvious things deserve the most scrutiny.**
When something seems clear or straightforward, that is precisely when to slow down. Obvious
conclusions are where unexamined assumptions accumulate. If a section is coming together
quickly and cleanly, that is a warning sign, not a sign of progress.

**Enumerate before committing.**
Any section that asks for a cause, plan, or solution requires multiple candidates before
converging. Pick the first plausible idea and you will frequently pick the wrong one.

**Steelman before dismissing.**
When arguing against a candidate, make the strongest case for it first. Dismissing a weak
version of an idea is not the same as ruling it out.

**Stay hedged until `<implementation>`.**
Use uncertain language — "I think," "one possibility," "this might be" — in every section
before implementation. Confident statements belong only in `<implementation>`.

**Revise out loud.**
If your assessment changes mid-section, write "wait" or "actually" and continue. Do not
delete — the revision is part of the analysis.

**Depth check before every section transition.**
Before moving to the next section, answer these explicitly:

- What did I almost miss or initially overlook in this section?
- What is the weakest part of my current conclusion?
- What would I investigate further if I had more time?
  If any answer reveals something unaddressed, handle it before continuing.

**After any result, update before acting.**
When a test fails or something unexpected comes back, return to the relevant protocol
section and update the analysis before taking the next action. Work out what the result
means. Do not move from a failed result directly to a new action.
