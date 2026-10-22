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
5. Create the fewest independently verifiable steps. Each states the change and
   its verification; add paths or dependencies only when they clarify execution.
6. Include compatibility, migrations, authorization, generated artifacts,
   observability, rollout, or rollback only when the impact requires them.
7. Cover every acceptance criterion without copying it into the plan.

## Output

Use a concise `## Plan` Markdown section in the Linear issue description:

```markdown
## Plan

1. Change `src/example.ts#symbol` to produce the required behavior; verify with
   the focused test or check.

### Blockers and decisions required
- Only a decision that must be resolved before implementation.
```

Keep each step to one sentence when practical. Do not repeat the ticket context,
acceptance criteria, impact rationale, or a separate approach summary. Omit
`### Blockers and decisions required` and rollout notes when unused. Return only
the `## Plan` section and never write to Linear or a repository artifact. The
`product-owner` skill owns all Linear operations and fields.

Do not create another issue, sub-issues, comments, or plan files; invent
requirements; resolve product decisions; modify production code; mark steps
complete; or change issue status.
