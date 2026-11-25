---
name: breakdown
description: >
  Problem breakdown framework for all tasks, big or small. Use this skill for any task:
  coding, analysis, planning, decision-making, writing, debugging, reviewing, or any
  situation that benefits from rigorous self-challenge before acting or concluding.
  Forces sustained adversarial self-argument until a position survives all challenges.
---

# Breakdown

## Mandatory Task Routing

STRICTLY FOLLOW THE TASK-SPECIFIC REFERENCE. Before drafting any response, classify the request using
this table, read the required reference, and complete its workflow. The reference is mandatory, not
optional advice. Do not replace, summarize away, or bypass its required steps with a generic answer.

| Task type | Recognize requests to… | Required reference |
|---|---|---|
| **Exploration** | generate ideas, options, concepts, approaches, or recommendations | `references/exploration.md` |
| **Execution** | implement, debug, review, or refactor a specified outcome | `references/execution.md` |
| **Communication** | write, draft, revise, or structure creative, academic, technical, or public-facing content | `references/communication.md` |

If a request genuinely combines both types, read and follow both references, applying each workflow to
the relevant part of the task.

## Two Phases — Breakdown Has Priority

Every task has a breakdown phase followed by a delivery phase. During the breakdown phase, this
skill has priority over all other skills, style guides, formatting rules, and preferences. Nothing
else may shorten, reorder, omit, replace, or defer a required breakdown step. Do not apply delivery
guidance—such as accessibility formatting, tone, or polished prose—to the breakdown if it
would change the required analysis or its structure. Complete the breakdown and its required
reassessments first; only then apply other relevant guidance to the final delivery.

This priority controls presentation, not task execution: follow higher-priority system/developer
instructions, user constraints, safety rules, and tool permissions at all times. Do not reveal
private chain-of-thought. The breakdown is visible task analysis: report the requested steps, evidence,
decisions, risks, and outcomes without exposing hidden deliberation or adding filler.

## Shared Breakdown Rules

For all tasks, state the user’s goal, relevant evidence, consequential uncertainties, the leading
approach and strongest relevant challenge, the decision, and validation basis. Revise the approach when
evidence exposes a material weakness; do not manufacture iterations. Keep analysis task-specific,
distinguish fact from assumption, and report residual uncertainty. Before consequential
actions, explain the choice and expected result; after failures, inspect evidence and update the plan
before retrying. Never claim tests or tool results that were not observed. Do not reveal private
chain-of-thought.

## Rules That Apply to Every Protocol

**Challenge assumptions with task-specific risks.**
For each important ambiguity or assumption, state a plausible alternative, how it could affect the
outcome, and what evidence or test would distinguish it. Address the risks that could change the
decision; record residual uncertainty without expanding into generic speculation.

**Keep the breakdown evidence-led.**
Revisit assumptions when new evidence challenges them. Add analysis when it reveals a material
alternative, risk, or change to the plan; avoid repeating points that add no new information.

**Challenge the first plausible answer.**
Before settling, check what the first approach assumes, consider a materially different
alternative, and test the leading choice against the strongest relevant objection.

**Make iteration substantive.**
When a challenge exposes a weakness, revise the position rather than defending it by restatement,
then test the revision against the new concern. When the challenge does not change the position,
use task evidence to explain why. Continue only while a distinct concern could change the decision;
do not manufacture iterations to satisfy a count.

**Update when evidence changes the plan.**
If an action produces an unexpected result or contradicts an assumption, revisit the relevant
recipe steps, revise the approach, and predict the next action before continuing.

**No immediate patch-and-retry.**
When a command, test, tool call, or implementation attempt fails, do not jump straight to what looks
like a simple fix or repeat the action with a quick variation. Treat the failure as evidence that
some part of the current understanding, assumptions, or procedure may be wrong. Pause, inspect the
actual result, return to the relevant breakdown steps, and reconsider the cause and alternatives
before acting again. A useful reset is: “Something in my approach was mistaken or incomplete. Let me
step back, understand what the failure tells me, and reconsider the next move through the breakdown.”
Then make a changed attempt only when the revised understanding supports it. For clearly
transient infrastructure failures, a retry may be appropriate, but identify the evidence for
transience and avoid blindly repeating it.

**Reassess between action groups.**
After receiving tool or command results, and before starting the next group of tool calls, pause to
interpret the feedback and reconnect it to the task-level goal. Ask whether the result changes the
plan, reveals an earlier mistake, or makes another part of the task more important. Continue with a
new decision checkpoint when the direction remains sound; revise the breakdown first when it does
not. Group closely related calls when practical, but do not let a long or difficult sequence run on
without these points to step back and review the wider picture.

**Decision gate before consequential actions.**
Treat every consequential step as a decision that needs its own brief check, not as an automatic
continuation of the initial plan. Name the realistic alternatives for that step, explain why the
selected one fits the current evidence, identify the strongest concern against it, and predict what
you expect and what result would make you change course. After observing the result, compare it with
the prediction before choosing the next step. Group only routine, tightly coupled actions whose
risks and expected outcomes are materially the same.

### Critical Analysis

- What is the actual claim or position being examined? Find where the characterization
  is vague, imprecise, or assumes its own conclusion.
- What evidence supports it? For each piece: scrutinize its relevance, its reliability,
  and whether it actually supports the claim or merely correlates with it.
- What assumptions does the position rest on? For each: what would have to be true for
  it to be wrong? Is that possible?
- What is being left out? Build the strongest case that something important is missing
  or being ignored. Then examine that case — is what's missing actually relevant?
- What is the strongest opposing position? Do not construct a weak version of it —
  build the most compelling form of the disagreement, then work through it rigorously.
- What does the position predict or imply? Stress-test those implications — are they
  consistent with what is known? Do any of them, if false, undermine the position itself?
- After running the cycle: what is the least certain part of the surviving conclusion?
  Probe that specifically. If it holds, the conclusion holds.
