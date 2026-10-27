# Thinking Guides

Questions worth working through per task type. Not a checklist — prompts to make sure
nothing important was skipped. Go as deep as the problem demands.

---

## Fixing a bug

**Understand the failure**
- What exactly is the reported behavior vs. what should be happening?
- What does the error or stack trace say, precisely? What does each part mean?
- Which parts of the code are actually involved — and which ones are you assuming are involved?

**Diagnose before concluding**
- What are the different things that could explain this? Push past the obvious first answer.
- For each candidate: what evidence supports it, and what evidence argues against it?
- What's your leading hypothesis — and what's the strongest argument that it's wrong?
- Trace the execution path step by step. Where exactly does it diverge from expected behavior?
- If your hypothesis is right, what else would you expect to see? Is that present?

**Design the fix**
- What are a few different ways to fix this? What are the tradeoffs of each?
- Does the fix address the root cause, or just mask the symptom?
- What's the strongest objection to your chosen fix? Have you answered it?
- What else could break?

**Verify before moving on**
- Trace through the fix with the original scenario. Does it actually work?
- What's the edge case most likely to break this?
- Is there anything about this fix you're not confident in? If so, address it.

---

## Reviewing code

**Understand what you're looking at**
- What is this code supposed to do?
- What assumptions does it seem to make about its inputs and environment?

**Read carefully**
- For each function or block: what does it claim to do vs. what does it actually do?
- Where are you slowing down because something feels off? That instinct is worth following.
- For anything suspicious: what's the most charitable reading — is it actually fine? If not, why not?

**Evaluate each issue**
- How bad is this in practice — what's the realistic worst case?
- Is there a scenario where this causes silent data corruption, or only a visible failure?
- What's the priority order if there are multiple issues?

**Before finishing**
- What's the single thing most important to fix?
- Is there anything you glossed over that deserves a second look?

---

## Writing new code

**Nail the requirements first**
- What are the inputs, outputs, and constraints? Be specific about types and edge cases.
- What's ambiguous or underspecified? Don't proceed past ambiguity — resolve it or flag it.
- What's the simplest input that would break a naive implementation?

**Design before writing**
- What are a few different ways to approach this? What are the tradeoffs?
- Which approach holds up best when you try to find its failure cases?
- How will edge cases be handled — null, empty, invalid, extreme, concurrent?
- What's your biggest design uncertainty? Address it before writing.

**Verify after writing**
- Trace through with a normal input. Right output?
- Trace through with an edge case. Graceful failure?
- Does it match what you described at the start? If not, which one is wrong?

---

## Debugging something unclear

**Inventory what you actually know**
- What do you know for certain vs. what are you assuming?
- When does this happen, and critically — when doesn't it? What differs between those cases?
- What does the stack trace point to? Is that the real source or a re-throw?

**Generate and challenge hypotheses**
- What are the distinct explanations for this behavior? Get past the first one.
- For each: what would you expect to see if it were true? Is that present or absent?
- What's your leading hypothesis — and what's the hardest question you can ask about it?
- What single observation would most definitively confirm or rule it out?

**Before fixing**
- Can you reproduce this deterministically? If not, fix that first.
- Are you fixing the root cause or the symptom?

---

## Refactoring

**Understand what must not change**
- What are the behavioral contracts — the observable inputs, outputs, and side effects
  that callers depend on?
- What are you most worried about breaking silently?

**Plan carefully**
- What's the order of changes that keeps each step independently verifiable?
- For each change: why is the new version behaviorally equivalent? Can you articulate it precisely?
- Which transformation is highest risk? Do that one last, or break it into smaller steps.

**Verify after**
- For each public interface: are inputs, outputs, and side effects identical?
- What edge case is most likely to have quietly changed behavior?
- If tests exist: would they catch a subtle behavioral change, or only a crash?
