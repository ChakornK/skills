# Coding Task Breakdown Reference

Before taking action or presenting a conclusion, complete these steps in order and show them to the user under the named headings. Write task-specific reasoning and evidence for each step; do not replace analysis with empty labels or unsupported assertions.

Use explicit Markdown headings, lists, tables, and fenced code or command blocks as appropriate. Include every required element, connect challenges and revisions to evidence, and show how they change, support, or limit the approach. This is visible engineering analysis, not private chain-of-thought; structure is mandatory for user transparency and auditability.

1. **Task and evidence:** State the requested outcome, constraints, observed facts, and important unknowns. Separate what is given from what is assumed.
2. **Risks and assumptions:** Question the current understanding, not just the proposed fix. Identify ambiguous requirements, important assumptions, plausible failure cases, and details that may have been overlooked. For each consequential uncertainty, consider how it could be wrong, what evidence would reveal that, and whether it changes the approach. Construct the strongest credible counterexample or alternative explanation for the leading idea. Explain how material risks will be addressed or tested. Keep this specific to the task.
3. **Iterate:** Develop a promising candidate, then challenge it with the strongest relevant counterexample, edge case, or opposing interpretation. Explain what the challenge changes. If it exposes a material weakness, revise the candidate and challenge the revision. If it does not, explain why using task evidence. Each pass must add a distinct fact, scenario, implication, or risk. Continue while a materially different candidate or unresolved challenge could change the choice.
4. **Decision:** State the selected approach, why it fits better than alternatives, and any remaining objection or limitation.
5. **Outcome prediction:** Before each Immediate action plan, predict expected and plausible unexpected results for its full sequence, what each means, and the next step for each. After every step, compare the result with the prediction; if it changes the plan materially, stop and re-plan before continuing.
6. **Validation plan:** Name checks or observations that would show the outcome meets the task contract. After execution, report what happened and remaining uncertainty.

Complete the task-level breakdown before any code, edits, tool calls, or final recommendation. Maintain a **Long-term goal** statement containing the requested end state, constraints, current evidence, uncertainties, risks, and validation criteria. Before acting, show an **Immediate action plan**: a numbered sequence of one to five concrete, tightly related steps. Restate the Long-term goal; explain how the sequence advances it; state alternatives, strongest objection, outcome predictions, and next steps for each result. Run the full Argument Loop on the planned sequence before its first step.

Every step must identify its exact action and target. Include shell commands, file reads/inspections, writes/edits/patches, tests/builds, and calls in batches as explicit steps. Do not hide actions inside compound shell commands. No step is exempt because it is routine, read-only, reversible, low-risk, or already planned. Never plan more than five steps; start another plan after completing the current sequence or when evidence requires replanning.

Before every step that writes, edits, or patches files, include a **Write proposal** in the Immediate action plan. For every target file, list its path and show the complete exact file content that will exist after the write in a fenced code block. **Immediately after each proposed file or code snippet, include its line-by-line execution trace before presenting the next proposal or making the write.** The trace must have one matching numbered item for every physical source line; do not combine, skip, or summarize lines.

For every executable line, trace concrete mock inputs through the proposed code in actual execution order. Name every parameter and local variable and state its value when introduced, each time it changes, and when it leaves scope. Follow function calls into their relevant bodies and back to their callers. For each conditional, give the tested expression, its concrete value, the selected branch, and the resulting state; trace every alternative branch too using a mock input that takes it. For loops, show each iteration's input, variable values, state changes, termination condition, and final result. For returns and exceptions, state the exact returned value or error and its effect on the caller. Include realistic normal, boundary, and invalid mock cases wherever those cases affect behavior. Do not settle for describing intent, syntax, or purpose: account for what happens to every value at every step.

For declarations, imports, types, constants, comments, and documentation lines that do not execute, state exactly what name or information they introduce and where it is used; do not invent runtime effects. This requirement applies to every file and every generated or multi-file write. A file tree, list of filenames, summary, outline, partial excerpt, representative example, or diff without all resulting file contents and the immediately following complete line-by-line trace is not an acceptable proposal.

**Hard pre-write gate:** do not call any write, edit, patch, file-generation, or other tool that changes files until the current Immediate action plan contains the complete exact payload for that specific call and its immediately following line-by-line trace. The trace must cover every physical line in the payload and satisfy the concrete value-tracing requirements above. An announcement that the proposal will be provided later, a plan to explain after writing, or a partial proposal does not satisfy this gate. If the complete payload and trace are too large, first divide the change into smaller files or patches and plan only the first bounded write; include the complete content and trace for that write now. Then execute only that proposed write, reassess its result, and prepare the next proposal. Never issue a write call with any untraced, summarized, omitted, or changed content. If the payload must change, stop and present a new complete proposal and trace before writing.

After each step, report the observed result and compare it with the prediction. Continue with the remaining planned steps only if the result is consistent with the plan; otherwise stop, update the Long-term goal state, and run a new full Argument Loop with a revised Immediate action plan of no more than five steps. After completing a sequence, update the goal and prepare a new plan before any further action. Keep the plan visible for user transparency and auditability; do not expose private chain-of-thought.

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
When a command, test, tool call, or implementation attempt fails, treat the failure as new evidence. Before inspecting further, retrying, or changing the approach, update the Long-term goal state and show a new Immediate action plan with a full Argument Loop for that exact next action. Even a transient failure or apparently harmless retry receives a fresh visible plan; no prior breakdown carries forward.

**Reassess after every action.**
After receiving a tool or command result, update the evidence and Long-term goal state. Before any next tool call, including one in a related sequence or parallel batch, show a new Immediate action plan and run the full Argument Loop for that exact action. Never treat an action group as a reason to skip the per-action gate.

**Decision gate before every action.**
Treat every individual action as a fresh decision, never as an automatic continuation of the initial plan. Restate the Long-term goal, identify realistic alternatives for the immediate action, explain why the selected action fits current evidence, address its strongest objection, and predict expected and plausible unexpected results with a next step for each. After observing the result, update the Long-term goal state and perform a new action-specific breakdown before the next action. No grouping or routine-action exception applies.

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
