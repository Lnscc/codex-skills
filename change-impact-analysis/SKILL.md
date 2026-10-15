---
name: change-impact-analysis
description: >
  Analyze an existing Linear engineering issue against its codebase and add an
  evidence-backed impact section. Use before planning or coding to identify
  affected code, interfaces, data, tests, risks, and open decisions. Do not
  create issues, plans, or production changes.
---

# Change Impact Analysis

Map the issue to the smallest evidence-backed set of affected areas.

## Analysis

1. Require an existing Linear issue identifier or URL; do not replace it with a
   prompt, diff, or plan.
2. Read repository guidance, the issue, and only relevant architecture context.
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
7. Record assumptions, issue conflicts, risks, and unresolved decisions. Do not
   invent product behavior or prescribe unnecessary abstractions.

## Output

Use a concise `## Impact` Markdown section in the Linear issue description:

```markdown
## Impact

### Summary
Expected blast radius and main risk.

### Affected areas
- `src/example.ts` — direct, confirmed: why it is affected; expected change.

### Interfaces and data
- None

### Verification
- Check that demonstrates the affected behavior.

### Assumptions and issue conflicts
- None

### Risks and decisions
- None

### Unknowns
- None
```

For every affected element, include scope (`direct`, `indirect`, or
`conditional`), confidence (`confirmed`, `inferred`, or `unknown`), reason, and
expected change. Add headings for modules, dependencies, operations, migrations,
or other concerns only when relevant. Avoid unsupported inventories.

Return the section without writing for read-only requests. When asked to update
the issue, replace only its `## Impact` section and preserve the title, fields,
and all other description sections. If Linear is unavailable, return the section
and state that it was not saved. Never create a separate artifact, comment, or
issue, and never modify production code.
