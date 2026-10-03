---
name: comment-guidelines
description: Apply these comment-writing and comment-editing rules whenever writing new comments or touching existing ones in any programming language (Rust, Python, JavaScript/TypeScript, Go, Java, C/C++, etc.). Use this skill any time code is being written, edited, or reviewed and comments are added, modified, or cleaned up — including docstrings, doc comments, and inline comments. Covers what comments should describe, what details must be preserved, formatting to avoid, and doc-comment vs implementation-comment conventions across languages.
---

# Comment Guidelines

A language-agnostic standard for writing and editing code comments. Apply these rules to every new or changed comment when modifying a file, regardless of the programming language.

## Rules

1. **Describe behavior, not history.** Comments explain what the code currently does. Avoid documenting past decisions, previous values, migration notes, or the reasoning trail that led to the current implementation. If context is genuinely necessary (e.g. a workaround for a specific bug), state it briefly as a present-tense fact ("Works around X doing Y"), not as a narrative.

2. **Preserve important details.** Edge cases, preconditions, return values, error-handling behavior, and side effects must stay when editing a comment. Condense wording without losing information.

3. **State limitations plainly.** Phrases like "best-effort cleanup," "silently ignores errors," or "not thread-safe" are acceptable and encouraged because they describe actual behavior.

4. **Remove decorative formatting.** No `---`, `===`, ASCII art, box-drawing borders, or section-divider lines inside comments. The language's standard documentation-comment syntax remains valid and should be kept.

5. **No specific benchmark numbers or magic counts.** Replace "tests 62k+ items" with "tests a large set." Remove hardcoded counts, timings, or sizes that a human maintainer wouldn't know or that will go stale, unless the number is actually part of the logic itself (e.g. a buffer size or a protocol constant).

6. **Use active voice and direct language.** Write "Validates the field" not "Performs validation on the field." Write "Discards partial files on mismatch" not "In order to ensure correctness, partial files are discarded."

7. **Match doc comments to interfaces, line comments to implementation.** Documentation comments describe what a function, type, class, or module does for its consumers — its contract. Regular inline/line comments explain *why* a particular line or block of implementation logic exists. Keep each in its lane:
   - Doc comment → public contract (inputs, outputs, behavior, constraints)
   - Line comment → local reasoning for a non-obvious implementation choice

8. **Review after editing.** Re-read each file after making changes to verify no details were lost and no comment became misleading or out of sync with the code it describes.

9. **Leave good comments alone.** Not every comment needs rewriting. If a comment is already concise, accurate, and natural, skip it.

10. **Match the codebase tone.** Comments should read like a high-quality production codebase for that language and ecosystem — clear, brief, and technically precise. Follow the idiomatic comment style of the language in use rather than importing conventions from another language.

11. **Never use a "ponytail:" prefix.** Comments must never start with "ponytail:" (in any casing). Remove this prefix entirely rather than just rewording around it.

## Applying these rules

When asked to write, edit, or clean up comments in a file (or as part of a larger code change):

1. Go comment-by-comment. For each new or modified comment, check it against rules 1–7 and 9–10.
2. Don't touch comments that weren't part of the change and are already fine (rule 9).
3. After all edits, do a final pass over the file per rule 8.
