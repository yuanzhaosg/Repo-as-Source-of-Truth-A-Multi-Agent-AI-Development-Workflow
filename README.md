# Repo-as-Source-of-Truth: A Multi-Agent AI Development Workflow

A practical workflow for building products with multiple AI tools without letting scattered chat history become the project memory.

Core idea:

> Do not make chat history the source of truth. Make the repository the source of truth.

This repository provides a lightweight operating model for using tools like ChatGPT, Claude, Codex, and GitHub together in a controlled, auditable way.

```text
Repo docs = source of truth
ChatGPT / Claude = thinking, critique, task shaping
Codex = implementation agent
GitHub branch / PR = execution record
```

The goal is not to have one AI do everything. The goal is to give each AI a clear role, clear boundaries, and a shared source of truth.

---

## Why this workflow exists

AI coding tools are powerful, but real product work breaks down when each session depends on scattered chat history.

Common failure modes include:

- changing product logic outside the requested task
- refactoring unrelated files
- silently changing scoring or decision rules
- injecting fixture data into production
- treating assumptions as facts
- overclaiming what evidence proves
- relying on stale chat history
- forgetting previous constraints
- making frontend changes when the task was backend-only

The fix is simple: put product decisions, constraints, task specs, and handoff notes inside the repo.

Then every AI agent reads the same source of truth before changing code.

---

## Recommended role split

### ChatGPT

Use for:

- product strategy
- task decomposition
- deciding the next narrow slice
- product requirement drafting
- customer / investor / report wording
- architecture trade-off discussion
- turning messy ideas into implementation-ready tasks

Think of ChatGPT as the product lead or solution architect.

### Claude

Use for:

- long-context critique
- second-opinion review
- red-team review
- narrative polish
- risk and edge-case review
- checking whether the product is overclaiming

Think of Claude as the reviewer, editor, or red-team partner.

### Codex

Use for:

- repository implementation
- code changes
- tests
- commits
- deployment verification

Think of Codex as the implementation engineer.

---

## Key principle

Do not let multiple AI coding agents edit the same branch at the same time.

If you want to compare implementation approaches, use separate branches:

```text
codex/backend-slice
claude/backend-alternative
```

Then compare the diffs or PRs.

One writer per branch.

---

## Repository structure

```text
AGENTS.md
CLAUDE.md
AI_WORKFLOW.md
PRODUCT_BOUNDARIES.md

 docs/
  architecture/
    evidence-led-workflow.md
    task-spec-template.md
  tasks/
    example-task.md
  handoffs/
    current-state.md
```

The exact file names are not sacred. What matters is that the repo contains:

1. permanent product rules
2. active task specs
3. current project state
4. AI-agent instructions
5. an execution record through branches, commits, and PRs

---

## Daily loop

```text
1. Define the next narrow slice with ChatGPT or Claude.
2. Save the task spec under docs/tasks/YYYY-MM-DD-task-name.md.
3. Ask Codex to read repo instructions and implement only that task.
4. Run tests.
5. Commit and push.
6. Ask ChatGPT or Claude to review the diff against the task and boundaries.
7. Codex fixes review comments.
8. Update docs/handoffs/current-state.md.
```

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

---

## Why it works

This workflow separates thinking, implementation, and review.

The repo becomes the memory.

The task file becomes the contract.

The branch becomes the execution record.

The PR or commit history becomes the audit trail.

Instead of relying on one long chat thread, every AI tool gets the same operating context from the repository.

---

## One-sentence summary

The best AI development workflow is not “which model is smartest?”

It is:

> Put the product rules and task specs in the repo, give each AI a clear role, and use GitHub as the execution record.
