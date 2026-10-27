# Thinking Guides

These are questions worth working through for each type of coding task.
They're not sections to fill out — they're prompts to make sure you've covered the
important ground. Work through what's relevant, skip what isn't, and go as deep as
the problem demands.

---

## Fixing a bug

Before diagnosing:
- What exactly is the reported behavior, and what should be happening instead?
- What does the error message actually say, word by word?
- Which parts of the code are involved?

Before settling on a cause:
- What are a few different things that could explain this? List them out.
- What does the evidence support, and what does it rule out?
- Trace the execution path to where it fails — where exactly does it go wrong?
- What's the most likely cause, and what's your best counterargument to it?

Before writing the fix:
- What are a couple of ways to fix this? What are the tradeoffs?
- Does the fix address the root cause, or just the symptom?
- What else could it break?

After writing the fix:
- Trace through the fix with the original failing scenario — does it work now?
- What edge case are you most worried about?

---

## Reviewing code

Before diving in:
- What is this code supposed to do?

Working through the code:
- For each function or block: what does the name/comment say it does, vs. what does it actually do?
- Where are the places you'd want to slow down and look more carefully?

For each potential issue:
- Is there a reading of this code where it's actually fine?
- How bad could this get in practice?

Before finishing:
- What's the single most important thing to fix?
- Is this code safe to ship, or does something need to change first?

---

## Writing new code

Before writing anything:
- What exactly does this need to do? What are the inputs, outputs, and constraints?
- What's ambiguous or underspecified? Surface it now.
- What's the simplest input that would break a naive implementation?

Designing:
- What are a couple of different ways to approach this? What are the tradeoffs?
- How will edge cases be handled — null, empty, invalid, extreme values?

After writing:
- Trace through with a normal input. Does it return the right thing?
- Trace through with an edge case. Does it fail gracefully?
- Does it match what you said it would do at the start?

---

## Debugging something unclear

Before theorizing:
- What do you actually know vs. what are you assuming?
- When does this happen, and when doesn't it?
- What does the stack trace actually point to?

Generating hypotheses:
- What are a few different explanations for this?
- Which ones does the evidence actually support?
- Which ones can you rule out, and why?

Narrowing down:
- What's the one thing that would most help you confirm or rule out the leading hypothesis?
- Can you reproduce this deterministically before trying to fix it?

---

## Refactoring

Before changing anything:
- What exactly makes this code hard to work with?
- What are the behavioral contracts that can't change?
- What are you most worried about breaking?

Planning changes:
- What's the order of changes that minimizes risk?
- For each change: why is the new version equivalent to the old one?

After refactoring:
- For each public interface: are inputs, outputs, and side effects identical?
- What edge case is most likely to have quietly changed behavior?
