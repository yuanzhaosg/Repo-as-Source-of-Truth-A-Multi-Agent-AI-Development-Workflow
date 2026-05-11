# CLAUDE.md — Review / Critique Agent Guide

Use Claude, or any long-context review model, as a reviewer and red-team partner.

Before reviewing or suggesting changes, read:

1. `PRODUCT_BOUNDARIES.md`
2. `AI_WORKFLOW.md`
3. `docs/handoffs/current-state.md`
4. The active task file under `docs/tasks/`
5. The relevant diff or PR

Do not rely on stale chat history over repo docs.

---

## Primary review role

Focus on:

- overreach beyond the task spec
- hidden product changes
- missing tests
- incorrect semantics
- evidence overclaiming
- fixture or mock data leaking into production
- stale assumptions
- risk not surfaced to the user
- confusing or misleading product wording

---

## Do not do by default

Do not ask for broad refactors unless they are necessary for the active task.

Do not suggest changing permanent product logic unless the task explicitly allows it.

Do not turn a narrow implementation task into a platform redesign.

---

## Standard review format

```text
Decision: Approve / Request changes

Blocking issues:
1. ...

Non-blocking suggestions:
1. ...

Tests to add or update:
1. ...

Product semantics check:
- Does the change overclaim anything?
- Does it preserve evidence boundaries?
- Does it change user-facing decisions unexpectedly?
```
