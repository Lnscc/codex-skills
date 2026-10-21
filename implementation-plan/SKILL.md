---
name: implementation-plan
description: >
  Turn an existing Linear issue and its impact section into the smallest
  executable implementation plan. Use to define ordered steps, dependencies,
  acceptance criteria, and verification before coding. Return the Plan section
  to the Product Owner; do not modify Linear, create requirements, redo impact
  analysis, or change production code.
---

# Implementation Plan

Plan only the work required by the issue and its evidence-backed impact.

## Planning

1. Require an existing Linear issue with complete `## Ticket` and usable
   `## Impact` sections. Report missing or unsafe prerequisites instead of
   guessing.
2. Read repository guidance and inspect referenced code only as needed to confirm
   the impact is current. Report conflicts.
3. Keep unresolved product decisions as blockers or explicit alternatives.
4. Use existing boundaries and extension points; avoid speculative abstractions
   and unrelated cleanup.
5. Create the fewest independently verifiable steps. Each states its outcome,
   affected areas, dependencies, acceptance criteria, and verification.
6. Include compatibility, migrations, authorization, generated artifacts,
   observability, rollout, or rollback only when the impact requires them.
7. Cover every issue acceptance criterion and trace every step to the ticket or
   impact section.

## Output

Use a concise `## Plan` Markdown section in the Linear issue description:

```markdown
## Plan

### Approach
Short implementation approach.

### Steps
1. **Concrete outcome**
   - Affected areas: `src/example.ts`
   - Depends on: None
   - Acceptance: Verifiable result
   - Verification: Check proving completion

### Assumptions
- None

### Blockers and decisions required
- None

### Rollout
- None
```

Keep the plan proportional to the change. Return only the `## Plan` section and
never write to Linear or a repository artifact. The `product-owner` skill owns
description updates, priority, status, epic placement, and all other issue
fields.

Do not create another issue, sub-issues, comments, or plan files; invent
requirements; resolve product decisions; modify production code; mark steps
complete; or change issue status.
