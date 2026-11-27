# Coding Task Breakdown Reference

## Authority and compliance

These are mandatory operating instructions for coding tasks. When you read this reference, follow every applicable requirement before acting; do not treat it as optional background advice or silently substitute a summary.

Before taking action or presenting a conclusion, complete and show these stages under headings:

### Task and evidence

State the requested outcome, constraints, observed facts, and important unknowns. Separate supplied facts from assumptions.

### Risks and assumptions

Identify ambiguities, assumptions, plausible failure cases, and overlooked details. For consequential uncertainties, state how they could be wrong, what evidence would distinguish alternatives, and whether they change the approach. Construct the strongest credible counterexample to the leading approach.

### Iterate

Develop a candidate, challenge it with distinct counterexamples or edge cases, and revise when an attack lands. Continue while a materially different concern could change the decision; do not manufacture repetitions.

### Decision

State the selected approach, why it fits better than alternatives, and remaining objections or limitations.

### Outcome prediction

Predict expected and plausible unexpected results for the Short-Term Action Plan, their implications, and next steps. After each action, compare the observed result with the prediction; stop and replan if the remaining sequence is invalidated.

### Validation plan

Name checks that determine whether the task contract is met. After execution, report actual results and remaining uncertainty.

## Long-Term Goal and Short-Term Action Plan

Maintain a **Long-term goal** containing the requested end state, constraints, current evidence, uncertainties, risks, and validation criteria. Present the visible breakdown in this order: Long-term goal, the task-specific stages above, then a **Short-Term Action Plan** containing one to five numbered, concrete, tightly related actions. Run the Argument Loop on the planned sequence before beginning it.

While the plan remains valid, proceed through its listed actions without repeating the full breakdown between each one. After each action, inspect and report its result, compare it with the prediction, and update the task state. If the plan is exhausted or evidence changes its assumptions, scope, risks, or next steps, present a new breakdown and plan before proceeding. Never take an unlisted action or a sixth action under one plan.

Each planned action must identify its exact operation and target, including reads, shell commands, writes, tests, builds, and batched calls. Do not hide independent operations in compound commands or vague labels.

## Mandatory Post-Write Trace and Self-Review

Immediately after every individual file-changing action—including each write, edit, patch, generated-file operation, or source-modifying shell command—inspect its actual diff/content. Before any next action or tool call, provide a numbered, step-by-step trace of the code actually changed, based on the observed diff. Use concrete mock values to follow meaningful data flow, calls, branches, loops, state changes, outputs, and errors. Then run the Argument Loop on that specific change: state the implementation claim, attack it with strong edge cases and unintended effects, defend with code evidence or revise the plan, and assess correctness against the task contract. If a tool call changes multiple files, audit each changed file before proceeding. A later combined review does not satisfy this requirement retroactively. Do not replace the trace or self-review with a generic summary. If the audit finds a defect or invalidates the remaining plan, stop and create a revised Short-Term Action Plan before further edits.

## Protocol Selection

| Task                                       | Protocol            |
| ------------------------------------------ | ------------------- |
| Fix a reported bug                         | `bug-fix`           |
| Find issues in existing code               | `code-review`       |
| Write new code from a description          | `code-generation`   |
| Diagnose an unclear or intermittent issue  | `deep-debug`        |
| Restructure code without changing behavior | `refactor`          |
| Evaluate a claim, plan, or decision        | `critical-analysis` |

Use the matching task-specific questions below. For tasks without a matching row, select the
closest protocol and adapt it to the task.

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
When an action fails, treat the failure as new evidence. Stop the current plan if the failure changes its assumptions or next steps; show an updated breakdown and Short-Term Action Plan before inspecting further, retrying, or changing the approach. A retry may remain in the current plan only if it was explicitly listed with a prediction and the failure does not invalidate the sequence.

**Reassess after every action.**
After each result, update evidence and task state. If the remaining actions in the current Short-Term Action Plan still apply, continue with the next one. If they do not, stop and prepare a new visible breakdown and plan before proceeding.

**Decision gate before each short-term plan.**
Treat each new short-term sequence as a fresh decision. Restate the Long-term goal, identify alternatives for the sequence, explain why it fits current evidence, address the strongest objection, and predict outcomes and next steps. Reassess after every listed action; renew the full breakdown only when the plan ends or new evidence invalidates it.

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
