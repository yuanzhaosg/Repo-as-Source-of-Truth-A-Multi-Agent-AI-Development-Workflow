# Task Spec Template

Use this template for every implementation task.

Save task specs under:

```text
docs/tasks/YYYY-MM-DD-task-name.md
```

---

# Task: [Task name]

Date: YYYY-MM-DD

Owner: [Human owner]

Implementation agent: Codex / other

Review agent: ChatGPT / Claude / other

---

## Goal

Describe the narrow outcome this task should achieve.

---

## Context

Explain why this task exists and what current behaviour is missing or incorrect.

Link to relevant files, issues, commits, or prior handoff notes.

---

## Non-goals

Do not:

- [forbidden change 1]
- [forbidden change 2]
- [forbidden change 3]

Be explicit. This section prevents agent overreach.

---

## Required behaviour

The implementation must:

1. ...
2. ...
3. ...

---

## Files likely to change

```text
path/to/file1
path/to/file2
path/to/test_file
```

This list is guidance, not permission to refactor the whole repo.

---

## Tests

Add or update tests for:

1. ...
2. ...
3. ...

Run:

```bash
# example
python3 -m unittest discover
npm test
```

---

## Acceptance criteria

The task is complete when:

- [ ] behaviour works
- [ ] tests pass
- [ ] no forbidden boundaries were changed
- [ ] output is reported clearly

---

## Deliverable

Report:

- files changed
- tests run
- commit hash
- deployment verification if relevant
- assumptions or unresolved gaps
