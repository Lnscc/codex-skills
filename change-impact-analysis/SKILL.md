---
name: change-impact-analysis
description: >
  Analyze an existing Markdown engineering ticket against its codebase and return
  an evidence-backed impact section. Use before planning or coding to identify
  affected code, interfaces, data, tests, risks, and open decisions. Do not
  create tickets, plans, or production changes.
---

# Change Impact Analysis

Map the ticket to the smallest evidence-backed set of affected areas.

## Analysis

1. Require an existing ticket; do not replace it with a prompt, diff, or plan.
2. Read repository guidance, the ticket, and only relevant architecture context.
3. Locate concrete entry points, then trace relevant callers, callees, shared
   types, persisted data, configuration, generated code, and tests.
4. Classify each impact as:
   - **direct**: required for the requested behavior;
   - **indirect**: connected to a direct impact;
   - **conditional**: depends on an explicit design choice.
5. Cite paths and symbols. Mark findings **confirmed**, **inferred**, or
   **unknown**, and explain non-obvious dependency paths.
6. Include compatibility, migrations, authorization, validation, caching,
   asynchronous work, observability, deployment, or generated artifacts only
   when relevant.
7. Record assumptions, ticket conflicts, risks, and unresolved decisions. Do not
   invent product behavior or prescribe unnecessary abstractions.

## Output

Use the repository convention when available. Otherwise return a proportional Markdown section:

```markdown
## Impact analysis

### Summary

Expected blast radius and main risk.

### Affected areas

- `src/example.ts#symbol` — direct, confirmed: reason; expected change

### Verification

- Check that proves the affected behavior.

### Risks and decisions

- Risk, unresolved decision, or unknown.
```

Add assumptions, ticket conflicts, interfaces, data, dependencies, operations, or unknowns only
when relevant. Keep the analysis proportional and avoid unsupported file inventories.

Return the section without writing for read-only requests. When asked to update the ticket,
replace only its impact-analysis section and preserve the rest of the Markdown file. Never create
a separate impact file or modify production code.
