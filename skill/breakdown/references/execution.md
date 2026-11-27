# Coding Task Breakdown Reference

## Authority and compliance

These are mandatory operating instructions for coding tasks. When you read this reference, follow every applicable requirement literally and unconditionally before acting; do not treat it as background advice, reinterpret it as optional, or let generic workflow preferences override it. In particular, never write, edit, patch, or generate a file without first presenting the required complete proposal and execution trace in the specified order. If a requirement applies, comply with it; do not silently omit, defer, abbreviate, or substitute a summary.

Before taking action or presenting a conclusion, complete these steps in order and show them to the user under the named headings. Write task-specific reasoning and evidence for each step; do not replace analysis with empty labels or unsupported assertions.

Use explicit Markdown headings, lists, tables, and fenced code or command blocks as appropriate. Include every required element, connect challenges and revisions to evidence, and show how they change, support, or limit the approach. This is visible engineering analysis, not private chain-of-thought; structure is mandatory for user transparency and auditability.

1. **Task and evidence:** State the requested outcome, constraints, observed facts, and important unknowns. Separate what is given from what is assumed.
2. **Risks and assumptions:** Question the current understanding, not just the proposed fix. Identify ambiguous requirements, important assumptions, plausible failure cases, and details that may have been overlooked. For each consequential uncertainty, consider how it could be wrong, what evidence would reveal that, and whether it changes the approach. Construct the strongest credible counterexample or alternative explanation for the leading idea. Explain how material risks will be addressed or tested. Keep this specific to the task.
3. **Iterate:** Develop a promising candidate, then challenge it with the strongest relevant counterexample, edge case, or opposing interpretation. Explain what the challenge changes. If it exposes a material weakness, revise the candidate and challenge the revision. If it does not, explain why using task evidence. Each pass must add a distinct fact, scenario, implication, or risk. Continue while a materially different candidate or unresolved challenge could change the choice.
4. **Decision:** State the selected approach, why it fits better than alternatives, and any remaining objection or limitation.
5. **Outcome prediction:** In the Short-Term Action Plan, predict expected and plausible unexpected results for the sequence, what each means, and next steps. After each action, compare its result with the prediction; continue through remaining listed actions while they remain valid, otherwise stop and re-plan.
6. **Validation plan:** Name checks or observations that would show the outcome meets the task contract. After execution, report what happened and remaining uncertainty.

Complete the task-level breakdown before any code, edits, tool calls, or final recommendation. Maintain a **Long-term goal** statement containing the requested end state, constraints, current evidence, uncertainties, risks, and validation criteria. Present the visible breakdown in this order: Long-term goal, all other task-specific breakdown sections, then a **Short-Term Action Plan** containing a numbered sequence of one to five concrete, tightly related actions. Run the full Argument Loop over that sequence before beginning it.

While the plan remains valid, execute its listed actions in order. After each action, inspect and report the result and compare it with the prediction. Do not repeat the full breakdown between listed actions when evidence leaves the remaining plan intact. When the plan is exhausted or new evidence changes its assumptions, risks, scope, or next steps, show a new breakdown in the required order followed by a new plan of one to five actions. Never take an unlisted action or a sixth action under one plan.

Every planned action must identify its exact operation and target, including shell commands, file reads/inspections, writes/edits/patches, tests/builds, and calls in batches. Do not hide independent work inside compound commands or vague action labels. Before a file-changing action, state the target path(s) and intended change in the Short-Term Action Plan; do not duplicate the full code payload in advance.

**Mandatory numbered trace and self-review after every file-changing action:** immediately after each individual write, edit, patch, generated-file call, or shell command that changes source or other project files, inspect that action's actual diff/content. Before any next action or tool call—including another edit, test, inspection, or shell command—show a detailed step-by-step trace of the code actually changed, based on the observed diff, not a planned or remembered version. Write the trace as an ordered numbered list, with separate numbered items for successive execution steps; do not replace it with prose paragraphs, grouped bullets, or a compressed summary. Use concrete mock values to walk through the changed logic's data flow, meaningful operations, calls, branches, state changes, loops, outputs, and errors. Then run the Argument Loop on that specific change: state the implementation claim, construct the strongest relevant attack (including edge cases and unintended effects), defend it with code evidence or revise the plan, and assess correctness and completeness against the task contract. If a tool call changes multiple files, audit every changed file before proceeding. A later combined review does not satisfy this per-action requirement retroactively. If the trace or self-review finds a defect or invalidates the remaining plan, stop and create a revised Short-Term Action Plan before further edits. Never substitute only a change summary, generic purpose statement, or trace of code that differs from the observed change.

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
