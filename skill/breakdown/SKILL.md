---
name: breakdown
description: >
  Problem breakdown framework for all tasks, big or small. Use this skill for any task:
  coding, analysis, planning, decision-making, writing, debugging, reviewing, or any
  situation that benefits from rigorous self-challenge before acting or concluding.
  Forces sustained adversarial self-argument until a position survives all challenges.
---

# Breakdown

## Required Recipe

Before taking action or presenting a conclusion, complete these steps in order. Use the named
headings so coverage is clear. Write enough task-specific detail to support each step; do not
replace analysis with a checklist of one-line answers or inflate it with repetition.

1. **Task and evidence:** State the requested outcome, constraints, observed facts, and important
   unknowns. Separate what is given from what is assumed.
2. **Scratchpad:** Surface task-specific uncertainties, assumptions to check, plausible failure
   cases, and details that may have been overlooked. For each important assumption behind the leading
   idea, ask how it could be false and what evidence would reveal that. Construct the strongest
   credible counterexample or alternative explanation you can, then compare it with the evidence and
   record whether it changes the approach or remains an unresolved risk. Use these challenges to
   generate or revise candidates; do not treat the scratchpad as a box to fill before moving on.
3. **Iterate:** Develop a promising candidate, then challenge it with the strongest relevant
   counterexample, edge case, or opposing interpretation. Explain what the challenge changes. If it
   exposes a material weakness, revise the candidate and challenge the revision. If it does not,
   explain why using task evidence. Update the scratchpad when a new concern or assumption emerges.
   Continue while a materially different candidate or unresolved challenge could change the choice;
   stop when another pass would only repeat what is already addressed. Make at least one meaningful
   revision, or explain why the initial candidate survived its strongest challenge.
4. **Decision:** State the selected approach, why it fits better than alternatives, and any
   remaining objection or limitation.
5. **Outcome prediction:** Before each consequential action, state the expected result, one plausible
   unexpected result, what each would mean, and the next step for each. If the result undermines the
   current approach, revise the plan before continuing.
6. **Validation plan:** Name the checks or observations that would show the outcome meets the task
   contract. After execution, report what actually happened and any remaining uncertainty.

Complete the breakdown before code, edits, tool calls, or a final recommendation. After new evidence
or a failed check, revisit the relevant steps before taking the next consequential action. Keep the
breakdown proportional to the task: completeness means addressing applicable steps with evidence,
not meeting a word count.

## Protocol Selection

| Task                                       | Protocol          |
| ------------------------------------------ | ----------------- |
| Fix a reported bug                         | `bug-fix`         |
| Find issues in existing code               | `code-review`     |
| Write new code from a description          | `code-generation` |
| Diagnose an unclear or intermittent issue  | `deep-debug`      |
| Restructure code without changing behavior | `refactor`        |
| Evaluate a claim, plan, or decision        | `critical-analysis` |

Use the matching task-specific questions below. For tasks without a matching row, select the
closest protocol and adapt it to the task.

## Rules That Apply to Every Protocol

**Treat the current position as provisional.**
Ask what evidence, assumption, or overlooked scenario could make it wrong. Identify at least one
credible way the leading approach could fail, and test that possibility against the available
evidence. If the challenge holds, revise the approach; if it does not, explain why and retain any
uncertainty that remains. Do not mistake confidence for evidence, and do not keep searching once
further challenges add no material information.

In the scratchpad, make this self-challenge visible: state the assumption, the strongest plausible
counterexample or alternative, the evidence for and against it, and its effect on the current
approach. Avoid generic doubts that cannot be tied to the task or checked against evidence.

**Keep the breakdown evidence-led.**
Revisit assumptions when new evidence challenges them. Add analysis when it reveals a material
alternative, risk, or change to the plan; avoid repeating points that add no new information.

**Challenge the first plausible answer.**
Before settling, check what the first approach assumes, consider a materially different
alternative, and test the leading choice against the strongest relevant objection.

**Update when evidence changes the plan.**
If an action produces an unexpected result or contradicts an assumption, revisit the relevant
recipe steps, revise the approach, and predict the next action before continuing.

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
