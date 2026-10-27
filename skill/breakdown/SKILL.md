---
name: breakdown
description: >
  Problem breakdown framework for coding tasks. Use this skill for any coding task:
  bug fixing, code review, writing new code, debugging intermittent issues, or refactoring.
  Requires a thorough written analysis and plan as part of every response, before any code.
---

# Breakdown

## Requirement

Every coding response begins with a written breakdown. This is part of the response, not
a preliminary to it. Code and actions come after. A breakdown that is short or thin is an
incomplete response — keep writing until you have genuinely exhausted the problem space.

## What a Breakdown Is

A breakdown is your written analysis of the problem: what you observe, what could explain
it, what the evidence supports, and what you plan to do. It is not a summary of the answer —
it is the work of finding the answer. Write it as the work unfolds, not after the fact.

**Go wide first.**
Before settling on any explanation or approach, lay out every plausible candidate. Not just
the obvious ones — push into less likely possibilities too. The right answer is often not
the first one, and you won't know which is right until you've compared them.

**Steelman before dismissing.**
When arguing against a candidate, make the strongest case for it first. Knocking down a
weak version of an idea is not the same as ruling it out. Each candidate should be taken
seriously before it's set aside.

**Challenge your own conclusions.**
Once you have a leading explanation or plan, argue against it. Find the flaw, the scenario
it doesn't cover, the assumption it's built on. If the challenge holds, revise. If it
doesn't survive after genuinely trying, you've earned confidence in it.

**The bar is "no remaining reasonable objection," not "sounds plausible."**
Keep going until you've addressed every objection you can raise. If something still feels
uncertain, name it and work through it. Short breakdowns mean the problem hasn't been
taken seriously enough.

**Revise as you go.**
If your assessment changes mid-breakdown, write "wait" or "actually" and continue. The
revision is part of the analysis, not a mistake to hide.

## After Results

When a test fails, a command returns something unexpected, or new information arrives —
update the breakdown before acting again. New evidence changes the analysis. Do not move
straight from a failed result to a new action; work out what the result means first.

## Task Guides

`references/thinking-guides.md` has questions worth covering for each type of coding task.
Use them to make sure nothing important was missed before moving to implementation.

## Hard Requirement

You must always provide an in-depth and detailed breakdown. You must always keep the user 
in the loop. Never ever take action without providing a breakdown. The user must always 
know what's going on.
