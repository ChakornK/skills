---
name: git-commit
description: Instruct agents to make conventional git commits after completing tasks
---

# Git Commit

## Overview
Creates a Git commit following proper standards.

**Announce at start:** "I'm using the git-commit skill to commit [change type and name]."

## The Process

### Step 1: Read Context

Before committing, verify:
- All modified files are intentional and complete
- No sensitive data or debugging code remains
- Tests pass and code is functional

---

### Step 2: Stage Files

Stage only the files relevant to this task:

```bash
git add <specific-files>
```

**Avoid:** `git add .` unless explicitly required.

---

### Step 3: Determine Commit Type

Select the appropriate conventional commit type based on changes:

| Type | Use Case |
|------|----------|
| `feat` | New features |
| `fix` | Bug fixes |
| `refactor` | Code refactoring without functional changes |
| `perf` | Performance improvements |
| `test` | Adding or updating tests |
| `docs` | Documentation changes |
| `style` | Code style changes (formatting, semicolons, etc.) |
| `chore` | Routine maintenance tasks |
| `ci` | CI/CD configuration changes |
| `build` | Changes to build system or dependencies |

---

### Step 4: Create Commit Message

Write a concise, imperative description (max 50 characters recommended):

**Format:** `<type>: <description>`

**Requirements:**
- One line only
- No scope (e.g., no `feat(scope):`)
- No description body
- No period at end
- Lowercase after colon

**Examples:**
```
feat: add user authentication
fix: resolve null pointer exception
refactor: simplify error handling
docs: update API documentation
test: add unit tests for login service
style: format code with prettier
chore: update dependencies
```

---

### Step 5: Execute Commit

Create the commit with the message:

```bash
git commit -m "<type>: <description>"
```

---

### Step 6: Verify Commit

Confirm commit was created successfully:

```bash
git log --oneline -1
```

Expected output should match format: `<type>: <description>`

---

### Step 7: Return Result

Report completion to parent agent:
- Confirm commit type used
- Confirm files committed
- Note any issues or warnings

---

## Remember

- **Context FIRST, commit SECOND**—verify changes before committing
- **Atomic commits**—one logical change per commit
- **Self-review is MANDATORY**—check message follows format exactly
- **Declarative messages**—use imperative mood ("add" not "added")
- **Return results to main agent**—report completion for orchestration

---

## Usage Examples

**After implementing a feature:**
```bash
git add src/auth.js
git commit -m "feat: add password reset endpoint"
```

**After fixing a bug:**
```bash
git add src/utils.js
git commit -m "fix: handle edge case in date parser"
```

**After refactoring:**
```bash
git add src/components/
git commit -m "refactor: extract validation utilities"
```

---

**Task**: Execute coding subtask: **$ARGUMENTS**
