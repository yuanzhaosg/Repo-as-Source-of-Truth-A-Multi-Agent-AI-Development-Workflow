# AI_WORKFLOW.md — Repo-as-Source-of-Truth Workflow

Repo docs are the source of truth.

Chat history is not the source of truth.

---

## Operating model

```text
Repo docs = source of truth
ChatGPT / Claude = thinking, critique, task shaping
Codex = implementation agent
GitHub branch / PR = execution record
```

---

## Roles

### ChatGPT

Use for:

- product strategy
- task decomposition
- evidence semantics
- investor / customer / report wording
- deciding the next narrow slice
- reviewing whether a change fits the product direction

### Claude

Use for:

- long-context critique
- second-opinion review
- red-team review
- overclaiming checks
- narrative polish
- edge-case analysis

### Codex

Use for:

- repo implementation
- tests
- commits
- deployment verification

---

## Branch discipline

Only one coding agent should edit a branch at a time.

If comparing alternatives:

```text
codex/task-name
claude/task-name
```

Then compare diffs or PRs.

One writer per branch.

---

## Daily loop

1. Define the next narrow slice.
2. Save the task spec under:

   `docs/tasks/YYYY-MM-DD-task-name.md`

3. Codex reads:

   - `AGENTS.md`
   - `PRODUCT_BOUNDARIES.md`
   - `AI_WORKFLOW.md`
   - `docs/handoffs/current-state.md`
   - the active task file

4. Codex implements only that task.
5. Codex runs tests.
6. Codex commits and pushes.
7. ChatGPT or Claude reviews the diff.
8. Codex fixes review comments.
9. Update `docs/handoffs/current-state.md`.

---

## Standard Codex prompt

```text
Read:
- AGENTS.md
- PRODUCT_BOUNDARIES.md
- AI_WORKFLOW.md
- docs/handoffs/current-state.md
- docs/tasks/[ACTIVE_TASK].md

Implement only the active task.
Do not change unrelated product logic.
Run listed tests.
Commit and push.

Report:
- files changed
- tests run
- commit hash
- deployment verification if relevant
```

---

## Standard review prompt

```text
Review this diff against PRODUCT_BOUNDARIES.md and the active task spec.

Focus on:
- overreach
- hidden product changes
- missing tests
- incorrect semantics
- fixture leakage
- stale assumptions
- changes outside scope

Return:
- approve / request changes
- blocking issues
- non-blocking suggestions
- tests that should be added
```
