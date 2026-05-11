# Task: Add Explicit Field Support Without Inference

Date: YYYY-MM-DD

Owner: Product owner

Implementation agent: Codex

Review agent: ChatGPT / Claude

---

## Goal

Add support for an explicitly supplied field in the backend workflow without inferring that field from weaker inputs.

This is an example task spec showing how to keep AI implementation work narrow and testable.

---

## Context

The product needs to use a field when it is directly supplied by a source document or user input.

However, the system must not infer the field from partial or weaker evidence.

---

## Non-goals

Do not:

- infer the field from adjacent data
- change scoring logic
- change valuation or recommendation logic
- change frontend behaviour
- inject fixture data into production
- refactor unrelated files

---

## Required behaviour

The implementation must:

1. Preserve the explicit field if it is present in the source payload.
2. Use the explicit field only where the task requires it.
3. Do nothing if the field is absent.
4. Avoid creating new missing-field noise when the field is absent.
5. Avoid using fixture data in normal production flow.

---

## Files likely to change

```text
backend/main.py
backend/structured_output.py
backend/tests/test_explicit_field.py
```

Replace these with actual project files.

---

## Tests

Add or update tests for:

1. explicit field is preserved
2. explicit field is used correctly
3. adjacent data does not trigger inference
4. missing explicit field is a no-op
5. fixture data is not injected
6. unrelated decision logic is unchanged

Run:

```bash
python3 -m unittest discover
```

---

## Acceptance criteria

The task is complete when:

- [ ] explicit field support works
- [ ] no inference is added
- [ ] tests pass
- [ ] product boundaries are preserved
- [ ] commit is pushed

---

## Deliverable

Report:

- files changed
- tests run
- commit hash
- unresolved gaps
