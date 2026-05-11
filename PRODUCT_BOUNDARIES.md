# PRODUCT_BOUNDARIES.md — Product Constraints Template

Use this file to capture permanent product constraints that AI agents must preserve.

These rules should be read before every implementation task.

---

## Core principle

> The system should do the analyst work and force the user to do the expert judgement work.

This means:

- Extract and organise evidence.
- Separate facts, assumptions, derived metrics, conflicts, missing evidence, and blocked decisions.
- Do not overclaim.
- Do not treat weak evidence as strong evidence.
- Do not silently change decision logic.

---

## Permanent no-change boundaries unless explicitly requested

Do not change:

- scoring logic
- valuation logic
- recommendation logic
- export behaviour
- memo / report behaviour
- frontend behaviour
- evidence semantics
- re-run / re-underwrite behaviour

Replace these examples with the boundaries relevant to your own product.

---

## Evidence rules

Public aggregate market data may be useful for:

- market benchmarking
- pricing context
- supply / demand context
- risk screening

Public aggregate market data is not, by itself:

- target-level evidence
- proof of revenue
- proof of profitability
- proof of demand
- proof of occupancy
- proof of customer waitlist
- proof of valuation

---

## Fixture rules

- Do not inject fixture data into production flow.
- Fixtures are test-only.
- Normal report flow must not silently include demo or test market data.

---

## Inference rules

- Do not infer missing facts unless explicitly requested.
- Prefer explicit source data first.
- Add automated inference only as a separate, tested slice.
- Surface uncertainty when data is incomplete.

---

## Scope control

Every task should state:

- goal
- non-goals
- files likely to change
- forbidden changes
- tests to run
- expected output

If a change is outside the task spec, do not make it.
