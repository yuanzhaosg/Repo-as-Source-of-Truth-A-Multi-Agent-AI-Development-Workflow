# AGENTS.md — Codex / Implementation Agent Rules

Before changing code, read:

1. `PRODUCT_BOUNDARIES.md`
2. `AI_WORKFLOW.md`
3. `docs/handoffs/current-state.md`
4. The active task file under `docs/tasks/`

Do not rely on stale chat history over repo docs.

---

## Working rules

- Keep each change narrow.
- Implement only the active task.
- Do not change product logic outside the active task.
- Do not refactor unrelated files.
- Do not silently change scoring, valuation, recommendation, export, reporting, or frontend behaviour.
- Do not inject fixture, mock, or demo data into production flow.
- Add or update tests for every behaviour change.
- Run the tests listed in the task before committing.
- Keep commits small and descriptive.

---

## Report back with

After implementation, report:

- files changed
- tests run
- commit hash
- deployment / health check result if relevant
- any assumptions or unresolved gaps

---

## Commit rules

Use small descriptive commits.

Examples:

```text
attach public market benchmark
extract explicit target fields
mark backend release
add manual override task spec
```

Do not commit:

- secrets
- local-only files
- generated reports
- temporary outputs
- fixture data in production paths

unless explicitly requested by the task.
