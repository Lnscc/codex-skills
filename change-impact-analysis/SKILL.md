---
name: change-impact-analysis
description: >
  Analyze an existing engineering issue against its codebase and produce an
  evidence-backed Impact section. Use before planning or coding to identify
  affected code, interfaces, data, tests, risks, and open decisions. Return
  content to the Product Owner; do not modify Linear, create issues or plans, or
  change production code.
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
5. Cite paths and symbols. State confidence only for inferred or unknown
   findings; confirmed findings need no label.
6. Include compatibility, migrations, authorization, validation, caching,
   asynchronous work, observability, deployment, or generated artifacts only
   when relevant.
7. Record assumptions, issue conflicts, risks, and unresolved decisions. Do not
   invent product behavior or prescribe unnecessary abstractions.

## Output

Use a concise `## Impact` Markdown section in the Linear issue description:

```markdown
## Impact

### Affected areas
- `src/example.ts#symbol` — direct: expected change and non-obvious reason.

### Risks and decisions
- Only material risk, conflict, unknown, or required decision.
```

For every affected element, include scope (`direct`, `indirect`, or
`conditional`) and expected change. Include a reason only when the relationship
is not obvious. Add confidence for anything not confirmed. Omit empty headings,
ticket summaries, acceptance criteria, verification steps, and unsupported
inventories.

Return only the `## Impact` section and never write to Linear or a repository
artifact. The `product-owner` skill owns description updates, priority, status,
epic placement, and all other issue fields. Never create a comment or issue, and
never modify production code.
