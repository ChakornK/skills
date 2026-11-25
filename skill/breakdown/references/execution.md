# Coding Task Breakdown Reference

Before taking action or presenting a conclusion, complete these steps in order. Use the named
headings so coverage is clear. Write enough task-specific detail to support each step; do not
replace analysis with a checklist of one-line answers or inflate it with repetition.

Write the breakdown as connected prose. Do not use Markdown headings, bolded subject labels, or
section-title formatting within it. Incorporate every required element naturally into the prose,
including the mental model and exact pre-action code trace; describe the code's inputs, outputs,
line-by-line behavior, and value-level execution without announcing them with a formatted label. Keep
challenges and revisions connected to the evidence and show how they change, support, or limit the
approach. This is visible engineering analysis, not a stream of private thoughts. The no-header style
does not waive, shorten, or replace any required breakdown element.

1. **Task and evidence:** State the requested outcome, constraints, observed facts, and important
   unknowns. Separate what is given from what is assumed.
2. **Risks and assumptions:** Question the current understanding, not just the proposed fix. Identify
   ambiguous requirements, important assumptions, plausible failure cases, and details that may have
   been overlooked. For each consequential uncertainty, consider how it could be wrong, what evidence
   would reveal that, and whether it changes the approach. Construct the strongest credible
   counterexample or alternative explanation for the leading idea. Explain how material risks will
   be addressed or tested. Keep this specific to the task rather than listing generic what-ifs.
3. **Iterate:** Develop a promising candidate, then challenge it with the strongest relevant
   counterexample, edge case, or opposing interpretation. Explain what the challenge changes. If it
   exposes a material weakness, revise the candidate and challenge the revision. If it does not,
   explain why using task evidence. Each pass must add a distinct fact, scenario, implication, or
   risk; a paraphrase of an earlier challenge is not another iteration. Update the risks and
   assumptions analysis when new concerns emerge.
   Continue while a materially different candidate or unresolved challenge could change the choice;
   stop when another pass would only repeat what is already addressed. Make at least one meaningful
   revision, or explain why the initial candidate survived its strongest challenge.
4. **Decision:** State the selected approach, why it fits better than alternatives, and any
   remaining objection or limitation.
5. **Mental model before action:** Before each consequential tool call that writes code, edits files,
   or executes code, show the exact code or command planned for that call. Explain what every line
   does; for shell commands, explain each command and significant argument. Label drafts as drafts and
   do not execute them until reviewed against the task and relevant risks. Before implementation,
   also specify each planned function/module’s responsibility, inputs, outputs, key logic, and how
   units interact. Trace representative inputs using exact values through branches, state changes, and
   outputs/errors, including a normal case and the most revealing edge or failure case. This is an engineering specification and execution trace, not private chain-of-thought. Resolve
   unclear flow or contracts before writing code.
6. **Outcome prediction:** Before each consequential action, state the expected result, one plausible
   unexpected result, what each would mean, and the next step for each. If the result undermines the
   current approach, revise the plan before continuing.
7. **Validation plan:** Name the checks or observations that would show the outcome meets the task
   contract. After execution, report what actually happened and any remaining uncertainty.

Complete the breakdown before code, edits, tool calls, or a final recommendation. Do not move from
the task-level breakdown straight into a sequence of unexamined choices. Before each consequential
decision or action, briefly record the specific choice, the alternatives that matter at that point,
the strongest relevant objection, the expected and plausible unexpected outcomes, and what you will
do for each. You may group tightly coupled routine choices when they share the same evidence and
risks; do not omit an independent consequential decision just because it fits the original plan.
For each consequential code-writing or code-execution tool call, include the exact planned snippet or
command and its line-by-line explanation immediately before the call; after execution, compare actual
results with the value-level trace and prediction.
After new evidence or a failed check, revisit the relevant steps before the next consequential
action. The breakdown is not a one-time preamble: return to it throughout the task so tool results
and intermediate changes do not narrow attention to the immediate obstacle or obscure the overall
goal. Keep it proportional: address each required point with task-specific evidence; do not replace
the breakdown with terse labels or repeat material that adds no new information.

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
