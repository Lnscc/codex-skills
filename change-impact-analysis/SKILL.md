---
name: change-impact-analysis
description: >
  Analyze an engineering ticket against its codebase and produce a temporary,
  evidence-backed impact assessment for planning or coding. Identify affected
  code, interfaces, data, tests, risks, and open decisions. Do not modify Linear,
  create issues or plans, persist the analysis, or change production code.
---

# Change Impact Analysis

Map the issue to the smallest evidence-backed set of affected areas.

## Analysis

1. Require an existing Linear issue identifier, URL, or a current ticket snapshot
   supplied by the caller. Do not fetch the issue again when the snapshot is
   sufficient.
2. Read repository guidance and only relevant architecture context.
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

Return a concise working analysis to the invoking agent:

```markdown
Impact

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

Return only the working analysis. Never write it to Linear, a comment, or a
repository artifact. Never modify production code.
