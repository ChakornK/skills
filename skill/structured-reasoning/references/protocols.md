# Reasoning Protocols

Follow the protocol for your task. All sections are mandatory.
The exploration rules in SKILL.md apply throughout — scratchpad first, enumerate before
committing, hedged language, revise out loud, red-team before each transition.

---

## bug-fix

**`<scratchpad>`**
Brain-dump everything you notice about the code and the bug report. Include things you're
unsure about, contradictions you spot, questions you'd want answered. No structure required.
Do not move on until you feel like you've exhausted your first-pass observations.

**`<analysis>`**
State only what you can directly observe — no hypotheses yet:
- What is the reported vs. expected behavior?
- What does each part of the error message or stack trace indicate?
- Which functions, lines, or data flows are visibly involved?
Every claim must reference a specific line, variable, or behavior from the actual code.

*Red-team:* What might you be misreading about the error or the code before moving on?

**`<root_cause>`**
List at least 3 possible causes. For each: what evidence supports it, what evidence
contradicts it. Then eliminate candidates one by one using the evidence. State your
conclusion as: "I think the most likely cause is [X] because [A, B] and [C, D] rule out
the alternatives — though I'm uncertain about [Y]."
Trace the execution path step by step to the point of failure.

*Red-team:* What would have to be true in the code for your leading hypothesis to be wrong?

**`<plan>`**
List at least 2 possible fixes. For each: why it would work, what risks it carries.
Choose one and explain why it's preferable to the alternatives. State every file and
function that will change.

*Red-team:* Could this fix address the symptom while leaving the root cause intact?

**`<implementation>`**
Write the complete fixed code. No abbreviations, no `[...]`. Multiple files get separate
comment headers. This is the only section where definitive, confident language is appropriate.

**`<verification>`**
Trace through the fix with the original bug scenario — what is the output now?
Trace through at least one edge case. State honestly whether any part of this fix
could cause regressions, and how confident you are overall.

---

## code-review

**`<scratchpad>`**
Read the code once through and write down everything you notice — suspicious patterns,
things you'd question, areas that look fine, things you're unsure about. No filtering.

**`<first_pass>`**
For each function or logical block:
- What it's supposed to do (name/comments)
- What it actually does (code)
- Any discrepancy between the two
No conclusions yet — only inventory.

**`<deep_analysis>`**
For each flagged area, trace the code path and state why it might be a problem.
Generate multiple interpretations before settling on a severity. Check: null/undefined
handling, off-by-one, async/race conditions, missing error handling, security, logic,
performance. Assign severity: Critical | High | Medium | Low | Nitpick.

*Red-team:* For each issue, is there a reading of the code where it's actually fine?

**`<findings>`**
List confirmed issues by severity. For each:
- **Issue:** short name
- **Severity:** level
- **Location:** file or function
- **Problem:** what is wrong
- **Fix:** how to address it, with a short snippet if helpful

**`<summary>`**
- Total counts by severity
- Single biggest risk in one sentence
- Recommendation: Ship as-is | Fix criticals first | Major rework needed

---

## code-generation

**`<scratchpad>`**
Think about the problem space before touching requirements. What's non-obvious about this?
What could go wrong? What similar problems have you seen, and how were they approached?

**`<requirements_check>`**
Restate the requirements in your own words:
- Inputs: types, formats, edge cases
- Outputs: types, formats, constraints
- Behavioral rules for each input type
- Explicit failure modes to prevent
Flag every ambiguity. Do not proceed past ambiguities — surface them here.

**`<design>`**
Generate at least 2 design approaches. For each: data structures, algorithm, how edge cases
are handled, tradeoffs. Choose one and explain why. Write pseudocode for any non-trivial logic.

*Red-team:* What input would break your chosen design?

**`<implementation>`**
Write the complete code based on the chosen design. Comment non-obvious logic.

**`<verification>`**
Trace through with: a normal input, an edge case, and an invalid input.
Does each produce the right output or fail gracefully?
Does the behavior match what you stated in `<requirements_check>`?

---

## deep-debug

**`<scratchpad>`**
Write everything you know, suspect, or are confused about. Include dead ends. Note what
you don't have enough information about. This is the most important section for this
protocol — do not rush it.

**`<evidence_gathering>`**
Inventory all evidence:
- Exact error message verbatim — analyze each word and phrase
- Stack trace — which frame is the real source vs. re-throw?
- When it occurs vs. when it doesn't (conditions, frequency, environment)
Mark each item: KNOWN (directly observed) vs. ASSUMED.

**`<hypothesis_generation>`**
Generate at least 3 hypotheses. For each:
- The hypothesis stated precisely
- Evidence supporting it
- Evidence contradicting it
- Plausibility: High | Medium | Low
Do not eliminate yet — just generate.

**`<elimination>`**
Work through each hypothesis against the full evidence set. Rule out what you can and
explain exactly why. For anything not fully ruled out, state what additional observation
would settle it. Conclude: "I think the most likely cause is [X] because [evidence],
though [Y] can't be fully ruled out without [Z]."

**`<plan>`**
- Minimal fix that addresses the root cause
- Guards or logging to add to prevent recurrence or confirm the fix
- How to reproduce deterministically before fixing, if possible

**`<implementation>`**
Write the fix and any added guards or logging.

**`<verification>`**
Does the fix address the root cause from `<elimination>`?
What would confirm it worked after the fix is deployed?
Any regression risk?

---

## refactor

**`<scratchpad>`**
Read the code and write down what bothers you about it, what's confusing, what you'd
want to change, and what you're worried about breaking. No filter.

**`<current_state_analysis>`**
- What does it do? (behavior — be precise about contracts)
- What makes it hard to read, maintain, or extend?
- What calls it, what does it call?
- What behavioral contracts are non-negotiable?

**`<refactor_plan>`**
List each transformation you'll make. Order them smallest to largest — smaller atomic
changes are safer. For each: why it improves the code, and why it's behaviorally equivalent.

*Red-team:* Which transformation is most likely to accidentally change behavior? How will you catch it?

**`<implementation>`**
Write the refactored code. Where equivalence is non-obvious, add a brief comment explaining why
this version behaves identically to the original.

**`<equivalence_check>`**
For each public function: confirm inputs, outputs, and side effects are identical.
Are there any edge cases where behavior might unintentionally differ?
Would existing tests pass? If not, which ones and why?
