# Evidence-Led Workflow Pattern

This pattern is useful for AI products that support decisions, analysis, diligence, reporting, or recommendations.

The key idea is to separate evidence from judgement.

---

## Principle

> Let the system do the analyst work. Make the human do the expert judgement work.

The system should:

- extract information
- identify sources
- show confidence and provenance
- separate found facts from assumptions
- flag missing evidence
- flag conflicts
- explain what is blocked
- prepare the user for the next decision

The system should not:

- pretend weak evidence is strong evidence
- hide missing data
- turn assumptions into facts
- overstate what public or aggregate data proves
- make final judgement look more certain than it is

---

## Evidence categories

A useful workflow often separates:

```text
found evidence
accepted evidence
derived evidence
conflicting evidence
excluded evidence
missing evidence
blocked underwriting / blocked decision inputs
```

You can adapt these categories to your own product.

---

## Why this matters for AI products

AI can generate polished outputs even when evidence is weak.

That creates a product risk: the output may look more reliable than the underlying data.

An evidence-led workflow reduces that risk by making the evidence trail visible.

---

## Example decision rule

Instead of:

```text
The opportunity is attractive.
```

Prefer:

```text
The opportunity may be attractive, but the conclusion is blocked until revenue, payroll, and occupancy evidence are verified.
```

Instead of:

```text
The market has demand.
```

Prefer:

```text
Public market data suggests realised usage in the area, but this is not proof of target-level occupancy or waitlist.
```
