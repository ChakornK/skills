# Protocols

Complete every section for your task. All sections are mandatory.
The rules in SKILL.md apply throughout — especially: your first answer is a draft,
the scratchpad is the longest section, and obvious things deserve the most scrutiny.

---

## bug-fix

**`<scratchpad>`**
Write everything you notice about the code and the bug report — including things you're
unsure about, contradictions, questions you'd want answered, and ideas you think are
probably wrong. Do not filter. Do not organize. Write until you start repeating yourself.
If you finish the scratchpad in under a page, you haven't gone deep enough — keep writing.

**`<analysis>`**
State only what you can directly observe — no hypotheses yet:

- What is the reported vs. expected behavior?
- What does each part of the error message or stack trace indicate, word by word?
- Which functions, lines, or data flows are visibly involved?
  Every claim must reference a specific line, variable, or behavior from the actual code.
  After your first pass, ask: what did I read too quickly? What am I assuming is clear when
  it might not be? Go back and examine those parts again.

_Depth check:_ What did I almost overlook? What is the least certain thing in this section?

**`<root_cause>`**
List at least 3 possible causes. For each: what evidence supports it, what evidence
contradicts it, and what would have to be true in the code for it to be correct. Do not
rush to eliminate — spend time genuinely making the case for each candidate, including
the ones you think are unlikely. Unlikely candidates are often where the real cause hides.
Then eliminate one by one using evidence. State your conclusion as: "I think the most
likely cause is [X] because [A, B] and [C, D] rule out the alternatives — though I'm
uncertain about [Y]." Trace the execution path step by step to the point of failure.
After stating your conclusion, argue against it. What is the best case that you're wrong?
If that case has merit, revise before continuing.

_Depth check:_ What would have to be true in the code for my leading hypothesis to be wrong?
What alternative did I dismiss too quickly?

**`<plan>`**
List at least 2 possible fixes. For each: why it would work, what risks it carries, and
what it would leave unaddressed. Do not settle for the first fix that seems reasonable —
reason about why it is strictly better than the alternatives, not just adequate. Choose one
and explain why it's preferable with specificity. State every file and function that will
change. Then ask: is there a version of this plan that is more conservative? Is there one
that is more thorough? Why is neither of those better than what you chose?

_Depth check:_ Could this fix address the symptom while leaving the root cause intact?
What is the riskiest assumption baked into this plan?

**`<implementation>`**
Write the complete fixed code. No abbreviations, no `[...]`. Multiple files get separate
comment headers. This is the only section where definitive, confident language is appropriate.
Before writing, re-read your plan and confirm you are implementing exactly what you decided —
not a simplified version of it.

**`<verification>`**
Trace through the fix with the original bug scenario step by step — what is the output at
each stage? Trace through at least two edge cases, not one. For each: what is the worst
thing that could happen? State honestly whether any part of this fix could cause regressions
and explain your reasoning, not just your conclusion. If your confidence is anything less
than high, state what would need to be true to raise it, and whether you can verify that now.

---

## code-review

**`<scratchpad>`**
Read the code once through and write down everything you notice — suspicious patterns,
things you'd question, things that look fine but deserve a second look, things you don't
understand yet, and things that seem obviously fine but that you should verify. Do not
filter. Write until you start repeating yourself.

**`<first_pass>`**
For each function or logical block:

- What it's supposed to do (name/comments)
- What it actually does (code)
- Any discrepancy between the two, however small
  No conclusions yet — only inventory. After your first pass, go back and read anything
  you moved through quickly. Speed is a sign you assumed rather than read.

_Depth check:_ What did I read too fast? What assumed I understood without checking?

**`<deep_analysis>`**
For each flagged area, trace the code path and state why it might be a problem.
Before settling on a severity, generate multiple interpretations — including the most
charitable reading of the code. Check exhaustively: null/undefined handling, off-by-one,
async/race conditions, missing error handling, security, logic, performance, and
assumptions about caller behavior. For each issue, ask: what is the worst realistic
outcome if this is never fixed? That determines severity.
Assign severity: Critical | High | Medium | Low | Nitpick.

_Depth check:_ For each issue — is there a reading of the code where this is actually fine?
Have I checked the callers and not just this function in isolation?

**`<findings>`**
List confirmed issues by severity. For each:

- **Issue:** short name
- **Severity:** level
- **Location:** file or function
- **Problem:** what is wrong and why it matters
- **Fix:** how to address it, with a short snippet if helpful

**`<summary>`**

- Total counts by severity
- Single biggest risk in one sentence
- Recommendation: Ship as-is | Fix criticals first | Major rework needed

---

## code-generation

**`<scratchpad>`**
Think about the problem space before touching requirements. What's non-obvious about this?
What could go wrong? What are the ways a naive implementation would fail? What edge cases
are probably not in the spec but matter anyway? Write until you've exhausted the problem space.

**`<requirements_check>`**
Restate the requirements in your own words:

- Inputs: types, formats, edge cases, invalid values
- Outputs: types, formats, constraints, failure cases
- Behavioral rules for each input type
- Explicit failure modes to prevent
  Flag every ambiguity. Do not proceed past ambiguities — surface them here. After your
  first pass, ask: what did I assume was specified when it actually wasn't?

_Depth check:_ What ambiguity am I proceeding past without flagging? What edge case did
I not account for in the requirements?

**`<design>`**
Generate at least 2 design approaches. For each: data structures, algorithm, how every
edge case from `<requirements_check>` is handled, and tradeoffs. Do not dismiss an
approach until you have fully articulated why it fails or is inferior — not just that
another approach is better. Choose one and explain why with specificity. Write pseudocode
for any logic that isn't obviously correct. After writing the pseudocode, trace through it
with the hardest edge case you identified.

_Depth check:_ What input would break my chosen design? What did I not account for?

**`<implementation>`**
Write the complete code based on the chosen design. Comment non-obvious logic. Before
writing, confirm the design handles every case in `<requirements_check>`.

**`<verification>`**
Trace through with: a normal input, the hardest edge case from your scratchpad, and an
invalid input. At each step, state what the code actually does — not what it should do.
Does the output match what you stated in `<requirements_check>`? If anything surprises
you during the trace, stop and fix it before continuing.

---

## deep-debug

**`<scratchpad>`**
Write everything you know, suspect, or are confused about. Include dead ends and ideas
you've already ruled out. Write down what you don't have enough information about and
what you would need to know to be more certain. This is the most important section —
do not rush it. If it's short, you haven't thought hard enough yet.

**`<evidence_gathering>`**
Inventory all evidence:

- Exact error message verbatim — analyze each word and phrase, not just the summary
- Stack trace — which frame is the real source vs. a re-throw? What does each frame tell you?
- When it occurs vs. when it doesn't — be precise about conditions, frequency, environment
- What changed recently, if anything
  Mark each item: KNOWN (directly observed) vs. ASSUMED. After your first pass, go back and
  re-examine anything you marked ASSUMED — can you verify it, or is it genuinely unknown?

_Depth check:_ What am I treating as known that is actually assumed? What evidence have
I not looked at closely enough?

**`<hypothesis_generation>`**
Generate at least 3 hypotheses. For each:

- The hypothesis stated precisely — not vaguely
- Evidence supporting it, referenced specifically
- Evidence contradicting it, referenced specifically
- Plausibility: High | Medium | Low, with reasoning
  Do not eliminate yet — just generate. Push past the obvious hypotheses. The correct
  explanation is often the third or fourth one you think of, not the first.

**`<elimination>`**
Work through each hypothesis against the full evidence set. Rule out what you can and
explain exactly why — not "this seems unlikely" but "this requires X to be true, and
the evidence shows X is false." For anything not fully ruled out, state what specific
observation would settle it. Conclude: "I think the most likely cause is [X] because
[evidence], though [Y] can't be fully ruled out without [Z]." Then argue against your
own conclusion — what is the strongest case that you're wrong?

_Depth check:_ Which hypothesis did I dismiss most quickly? Was that dismissal rigorous?

**`<plan>`**

- Minimal fix that addresses the root cause as identified in `<elimination>`
- Guards or logging to add to prevent recurrence or confirm the fix worked
- How to reproduce deterministically before fixing — if you can't reproduce it, the fix
  is a guess, and you should state that explicitly

**`<implementation>`**
Write the fix and any added guards or logging.

**`<verification>`**
Does the fix address the root cause from `<elimination>`, specifically?
What would confirm it worked after deployment — and would you be able to tell?
Any regression risk?

---

## refactor

**`<scratchpad>`**
Read the code and write down everything that bothers you, everything that's confusing,
everything you'd want to change, and everything you're worried about breaking. Do not
filter. Write until you've exhausted the space.

**`<current_state_analysis>`**

- What does it do? (behavior — be precise about every contract, not just the happy path)
- What makes it hard to read, maintain, or extend? Be specific — not "it's messy" but
  "function X does three unrelated things, which means Y"
- What calls it, what does it call, and what do callers assume about it?
- What behavioral contracts are non-negotiable? List every one explicitly.

_Depth check:_ What assumption about caller behavior am I making that I haven't verified?
What contract did I almost overlook?

**`<refactor_plan>`**
List each transformation you'll make. Order them smallest to largest — smaller atomic
changes are safer and easier to verify independently. For each: why it improves the code,
why it's behaviorally equivalent, and what could go wrong. After planning, ask: is there
a more conservative version of this plan that gets most of the benefit with less risk?
If so, why isn't that better?

_Depth check:_ Which transformation is most likely to accidentally change behavior?
How exactly will you verify it didn't?

**`<implementation>`**
Write the refactored code. Where equivalence is non-obvious, add a comment explaining
why this version behaves identically to the original. Before writing each transformation,
re-read the corresponding entry in `<refactor_plan>` to confirm you're implementing
exactly what you decided.

**`<equivalence_check>`**
For each public function: confirm inputs, outputs, and side effects are identical —
not in general, but for every case in the contract you listed in `<current_state_analysis>`.
Are there any edge cases where behavior might unintentionally differ, even in ways callers
currently don't depend on? Would existing tests pass? If not, which ones and why — and
does that reveal a contract you thought was safe to change but isn't?
