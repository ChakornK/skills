---
name: breakdown
description: >
  Problem breakdown framework for coding tasks. Use this skill for any coding task:
  bug fixing, code review, writing new code, debugging intermittent issues, or refactoring.
  Forces sustained adversarial self-argument before any action until a position survives
  all challenges.
---

# Breakdown

## The Argument Loop

Before every action, you must argue yourself to certainty. Not confidence — certainty.
The way you get there is not by thinking carefully once. It is by proposing a position,
attacking it, defending or revising it, then attacking it again. You repeat this until
you have made your best attempt to destroy the position and failed. Only then do you act.

The loop:

```
1. State a position — a diagnosis, cause, plan, or decision
2. Attack it — find the strongest possible objection you can construct
3a. If the attack lands: revise the position. Return to 1.
3b. If the attack doesn't land: explain precisely why not.
     Then construct a harder attack. Return to 2.
4. The loop ends only when a full round of attacks produces nothing
   that has not already been answered.
```

This is not a formatting exercise. The attacks must be genuine. A weak attack followed
by an easy defense is not a loop iteration — it is avoidance. The attack should be the
strongest version of the objection you can build, not a straw man constructed to be
knocked down. If you find yourself winning too easily, you are not attacking hard enough.

Write the argument out in full. Every proposal, every attack, every defense. Do not
summarize the loop after running it internally — the written argument is the work, not
a record of work done elsewhere.

## Exit Conditions

You may leave the loop only when both of the following are true:

**1. The last full round of attacks produced no new objection.**
Not "no strong objection" — no new objection at all. If you are still generating attacks
that require a response, the loop is not done.

**2. You have explicitly tried to find the objection that breaks your position and failed.**
This means you have considered alternatives you believe are wrong, edge cases you think
will not occur, and assumptions you believe are safe — and you have stated why each of
them does not defeat the position. If you have not done this, you have not tried hard enough.

Feeling confident is not an exit condition. Reaching a conclusion is not an exit condition.
Having written a lot is not an exit condition. The loop ends when the attacks have stopped
producing anything new — not before.

## Decision Gate — Before Every Action

Before taking any action — editing a file, running a command, calling a tool — run the
argument loop on the action itself:

- What are all the other actions you could take instead? Name them.
- Why is this action strictly better than each alternative? Not "better" — strictly better.
  State the specific reason each alternative is inferior or ruled out.
- What is the strongest argument that this action is wrong? Answer it.
  If you cannot answer it, do not act — you have not won the loop yet.

No action is exempt. No action is too small or too obvious to skip this gate.

## What to Argue About

The loop needs material. Below are the core questions for each type of task. Feed them
into the loop as starting positions or as attacks. They are not sections to complete —
they are the substance of the argument.

---

### Bug Fix

- What is the actual failure? Not the symptom — the precise mechanism. Attack any
  characterization of the failure that is imprecise or assumed.
- What are all the possible causes? For each: build the strongest case that it is the
  cause, then attack that case. Keep generating candidates until the loop produces none
  that survive challenge.
- What is the execution path from entry to failure? Attack every assumption in the trace.
- What is the fix? For every proposed fix: attack its completeness (does it address the
  root cause or just the symptom?), its safety (what does it break?), and its necessity
  (is there a simpler fix that is strictly equivalent?). Defend or revise until one fix
  survives all attacks.
- After implementing: trace through the fix. Attack the trace — find the scenario where
  it still fails. If you find one, return to the loop.

---

### Code Review

- What does each function actually do vs. what it claims to do? Attack any assumption
  that the name and behavior align.
- For every suspicious area: build the case that it is a real bug, then attack that case.
  Is there a reading of the code where it is correct? Attack that reading too.
- For every issue: attack the severity. Could this be worse than rated? Is there a
  scenario where this becomes a production incident?
- What did you read too quickly? Go back and attack your first-pass assumptions.

---

### Code Generation

- What are the actual requirements? Attack every assumption about unspecified behavior —
  what happens at the edges, with invalid input, under failure, with concurrent access?
- For each design: build the case that it is the best approach, then attack it. What
  input breaks it? What requirement does it mishandle? Defend or discard.
- After designing: attack the pseudocode. Find the case it does not handle.
- After implementing: trace through with the hardest input identified. Attack the output —
  is it actually correct, or does it only look correct?

---

### Deep Debug

- What do you actually know vs. what are you assuming? Attack every assumption — what
  would have to be true for it to be wrong?
- For each hypothesis: build the strongest case that it is the cause, then attack it with
  every piece of contradicting evidence. Do not dismiss a hypothesis until the attack is
  rigorous, not just convenient.
- What is the most uncomfortable hypothesis — the one requiring the most work to fix?
  Attack your reasons for dismissing it. Are you dismissing it because evidence rules it
  out, or because you do not want it to be true?
- After identifying the cause: attack the identification. What would you expect to see
  differently if the real cause were something else entirely?

---

### Refactor

- What are the behavioral contracts? For each: attack the assumption that callers do not
  depend on undocumented or accidental behavior. What if they do?
- For each transformation: build the case that it is behaviorally equivalent, then attack
  that case. Find the edge case where the new version behaves differently.
- After planning: attack the order of changes. Is there a sequence where an earlier
  change makes a later one harder to verify or introduces a window of broken behavior?
- After implementing: for each public function, attack the claim that behavior is
  identical. Trace through with an edge case not yet checked.

---

## After Results

When a test fails, a command returns unexpectedly, or new information arrives — treat it
as a new attack on your current position. Return to the loop with the result as the
opening challenge. Do not move to the next action until the loop has run on what you
just learned.
