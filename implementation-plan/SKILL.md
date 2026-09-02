---
name: implementation-plan
description: >
  Turn an existing YAML ticket and its impact mapping into the smallest
  executable implementation plan. Use to define ordered subtasks, dependencies,
  acceptance criteria, and verification before coding. Do not create
  requirements, redo impact analysis, or modify production code.
---

# Implementation Plan

Plan only the work required by the ticket and its evidence-backed impact.

## Planning

1. Require the complete ticket and a usable top-level `impact` mapping. Report
   missing or unsafe prerequisites instead of guessing.
2. Read repository guidance and inspect referenced code only as needed to confirm
   the impact is current. Report conflicts.
3. Keep unresolved product decisions as blockers or explicit alternatives.
4. Use existing boundaries and extension points; avoid speculative abstractions
   and unrelated cleanup.
5. Create the fewest independently verifiable subtasks. Each states its outcome,
   affected areas, dependencies, acceptance criteria, and verification.
6. Include compatibility, migrations, authorization, generated artifacts,
   observability, rollout, or rollback only when the impact requires them.
7. Cover every ticket acceptance criterion and trace every subtask to the ticket
   or impact mapping.

## Output

Use the repository schema when available. Otherwise return:

```yaml
plan:
  summary: Short implementation approach
  assumptions: []
  blockers: []
  decisionsRequired: []
  subtasks:
    - id: PROJECT-123-1
      title: Concrete outcome
      status: planned
      outcome: What this leaves working
      affectedAreas: []
      dependsOn: []
      acceptanceCriteria:
        - Verifiable result
      verification:
        - Check proving completion
  rollout: []
```

Keep empty lists as `[]` and the plan proportional to the change. Return it
without writing for read-only requests. When asked to update the ticket, replace
only its top-level `plan` mapping, preserve all other fields, and validate the
YAML.

Do not create a second ticket or plan file, invent requirements, resolve product
decisions, modify production code, mark subtasks complete, or change ticket
status without a separate request.
