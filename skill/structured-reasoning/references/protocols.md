# Reasoning Protocols

Follow the protocol for your task type exactly. All sections are mandatory.
Do not output any code until every pre-implementation section is complete.
Every claim must reference a specific line, variable, or behavior from the actual code —
no generic statements.

---

## bug-fix

Use when: a specific bug has been reported.

**Step 1 — `<analysis>`**
Re-read the code and bug report. State only what you can directly observe:
- What is the reported behavior?
- What is the expected behavior?
- What does the error message or stack trace indicate, word by word?
- Which functions, lines, or data flows are involved?
No hypotheses yet — only observations.

**Step 2 — `<root_cause>`**
Trace the execution path that leads to the failure:
- Walk through the code step-by-step from entry point to the point of failure.
- Identify the exact line or logic that produces the wrong behavior.
- State the root cause as: "The bug is caused by [X] because [Y]."
- Rule out at least one alternative explanation and state why it doesn't fit.

**Step 3 — `<plan>`**
Before writing any code:
- Describe the fix in plain English.
- Explain why this fix addresses the root cause, not just the symptom.
- List every file or function that will change.
- Note any risks or side effects.

**Step 4 — `<implementation>`**
Write the fixed code. Show the complete function or section — no abbreviations, no `[...]`.
If multiple files change, separate them with a comment header per file.

**Step 5 — `<verification>`**
Confirm the fix works:
- Trace through the fixed code with the original bug scenario. What is the output now?
- Identify at least one edge case and trace through that too.
- State whether the fix could cause regressions elsewhere.

---

## code-review

Use when: finding bugs or issues in existing code.

**Step 1 — `<first_pass>`**
Read the code top to bottom. For each function or logical block note:
- What it is supposed to do (from its name or comments)
- What it actually does (from the code itself)
- Any discrepancy between the two
No conclusions yet — only inventory.

**Step 2 — `<deep_analysis>`**
Investigate every flagged area and any other suspicious logic:
- Trace the code path for each issue candidate and state why it is a problem.
- Check: null/undefined handling, off-by-one errors, async/race conditions,
  missing error handling, security issues, incorrect logic, performance.
- Assign severity: Critical | High | Medium | Low | Nitpick

**Step 3 — `<findings>`**
List all confirmed issues by severity. For each:
- **Issue:** short name
- **Severity:** Critical | High | Medium | Low | Nitpick
- **Location:** file or function name
- **Problem:** what is wrong
- **Fix:** how to address it, with a short code snippet if helpful

**Step 4 — `<summary>`**
- Total issue count by severity
- The single biggest risk in one sentence
- Recommendation: Ship as-is | Fix criticals first | Major rework needed

---

## code-generation

Use when: writing new code from a description or requirements.

**Step 1 — `<requirements_check>`**
Restate the requirements:
- What inputs will this code receive? (types, formats, edge cases)
- What outputs must it produce? (types, formats, constraints)
- What are the behavioral rules for each input type?
- What must not happen? (failure modes to prevent)
Flag any ambiguities before proceeding.

**Step 2 — `<design>`**
Plan the implementation:
- What data structures and why?
- What is the high-level algorithm or flow?
- How will edge cases be handled (null, empty, invalid input)?
- What helper functions or modules are needed?
Write pseudocode for any non-trivial logic.

**Step 3 — `<implementation>`**
Write the complete code based on the design above.
Comment any non-obvious logic. Do not abbreviate.

**Step 4 — `<verification>`**
- Trace through with a normal input. What does it return?
- Trace through with an edge case. What happens?
- Trace through with invalid input. Does it fail gracefully?
- Does the output match the requirements in `<requirements_check>`?

---

## deep-debug

Use when: a bug is intermittent, unclear, or has no obvious cause.

**Step 1 — `<evidence_gathering>`**
List every piece of evidence:
- The exact error message, verbatim — analyze each word
- The stack trace — which frame is the actual source vs. a re-throw?
- The code paths involved
- When does it occur? (always, randomly, under load, after N calls)
- When does it not occur? (what conditions prevent it)
Mark each item as KNOWN (directly observed) or ASSUMED.

**Step 2 — `<hypothesis_generation>`**
Generate at least 3 hypotheses. For each:
- State the hypothesis clearly
- List evidence that supports it
- List evidence that contradicts it
- Rate plausibility: High | Medium | Low

**Step 3 — `<elimination>`**
Eliminate hypotheses against the evidence:
- Which are ruled out, and exactly why?
- What additional information would settle any remaining uncertainty?
- Which single hypothesis best fits all evidence?
Conclude: "The most likely cause is [X] because [A, B, C] and nothing contradicts it."

**Step 4 — `<plan>`**
- What is the minimal fix that addresses the root cause?
- What guards or logging should be added to prevent recurrence?
- Is there a way to reproduce the bug deterministically before fixing it?

**Step 5 — `<implementation>`**
Write the fix and any added guards or logging.

**Step 6 — `<verification>`**
- Does the fix address the root cause from `<elimination>`?
- Could this cause regressions?
- What would confirm the fix worked after deployment?

---

## refactor

Use when: restructuring code without changing observable behavior.

**Step 1 — `<current_state_analysis>`**
Describe the existing code:
- What does it do? (behavior)
- What are its problems? (readability, maintainability, structure)
- What are its dependencies? (what calls it, what does it call)
- What behavioral contracts must be preserved exactly?

**Step 2 — `<refactor_plan>`**
- List each transformation you will make
- State what you will not change
- Order the changes from smallest to largest for safety
- Explain how each change improves the code

**Step 3 — `<implementation>`**
Write the refactored code. For any non-obvious transformation, add a brief comment
explaining why it is behaviorally equivalent to the original.

**Step 4 — `<equivalence_check>`**
- For each public function or method, confirm inputs, outputs, and side effects are identical.
- Are there any edge cases where behavior might differ, even unintentionally?
- Would existing tests still pass? If not, which ones and why?
