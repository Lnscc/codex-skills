---
name: implementation-plan
description: >
  Turn an engineering ticket and its working impact analysis into the smallest
  executable implementation plan. Use to define ordered steps, dependencies,
  acceptance coverage, and verification before coding. Keep the plan temporary;
  do not modify Linear, create requirements, redo impact analysis, persist the
  plan, or change production code.
---

# Implementation Plan

Plan only the work required by the issue and its evidence-backed impact.

## Planning

1. Require a current ticket snapshot and usable working impact analysis.
   Report missing or unsafe prerequisites instead of guessing. Do not fetch the
   issue again when the supplied snapshot is sufficient.
2. Read repository guidance and inspect referenced code only as needed to
   confirm the impact is current. Report conflicts.
3. Keep unresolved product decisions as blockers or explicit alternatives.
4. Use existing boundaries and extension points; avoid speculative abstractions
   and unrelated cleanup.
5. Create the fewest independently verifiable steps. Each states the change and
   its verification; add paths or dependencies only when they clarify execution.
6. Include compatibility, migrations, authorization, generated artifacts,
   observability, rollout, or rollback only when the impact requires them.
7. Cover every acceptance criterion without copying it into the plan.

## Output

Return a concise working plan to the invoking agent:

```markdown
Plan

1. Change `src/example.ts#symbol` to produce the required behavior; verify with
   the focused test or check.

### Blockers and decisions required
- Only a decision that must be resolved before implementation.
```

Keep each step to one sentence when practical. Do not repeat the ticket context,
acceptance criteria, impact rationale, or a separate approach summary. Omit
`### Blockers and decisions required` and rollout notes when unused. Return only
the working plan and never write it to Linear, a comment, or a repository
artifact.

Do not create another issue, sub-issues, comments, or plan files; invent
requirements; resolve product decisions; modify production code; mark steps
complete; or change issue status.
