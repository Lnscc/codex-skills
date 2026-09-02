---
name: implementation-plan
description: >
  Turn an existing YAML engineering ticket and its `impact` mapping into an
  ordered, executable implementation plan with scoped subtasks, dependencies,
  acceptance criteria, and verification. Use when the user asks how a ticket
  should be implemented, wants work broken down, or needs a plan before coding.
  The plan is returned as a `plan` mapping for that same ticket and is written there
  only when requested. This skill plans work; it does not create requirements,
  analyze architectural impact from scratch, or modify production code.
---

# Implementation Plan

Translate the ticket's accepted requirements and evidence-backed impact into the
smallest complete sequence of implementation work. The ticket remains the source
of truth; the plan must not quietly expand or reinterpret it.

## Planning

1. Locate and read the complete ticket. Require a top-level `impact` mapping or
   an equivalent repository-defined impact analysis. If it is missing or too
   incomplete to plan safely, report that prerequisite instead of guessing the
   affected architecture.
2. Read repository guidance and inspect the referenced code only as needed to
   verify that the impact analysis is still current. Report stale or conflicting
   evidence; do not silently redo the ticket's requirements.
3. Identify open decisions that materially change the plan. Preserve them as
   blockers or explicit alternatives rather than choosing product behavior on
   the user's behalf.
4. Define an implementation approach that uses existing project boundaries and
   extension points. Avoid speculative abstractions and unrelated cleanup.
5. Break the work into the fewest independently verifiable subtasks that make
   sequencing and ownership clear. Each subtask must state:
   - its concrete outcome;
   - affected locations or components;
   - dependencies on other subtasks;
   - subtask acceptance criteria;
   - the verification needed to prove completion.
6. Cover relevant cross-cutting work identified by the impact analysis, such as
   compatibility, migrations, generated artifacts, authorization, observability,
   rollout, and rollback. Do not add categories that do not apply.
7. Check that every ticket acceptance criterion is covered by at least one
   subtask and that every subtask traces back to the ticket or impact analysis.

## Output

Return a `plan` YAML mapping containing:

- a short approach summary;
- assumptions, blockers, and decisions still required;
- ordered subtasks with stable local IDs;
- explicit `Depends on` relationships where ordering matters;
- acceptance criteria and verification for each subtask;
- rollout or migration notes only when relevant.

Use the repository's existing schema when one exists. Otherwise use:

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
      outcome: What this subtask leaves working
      affectedAreas: []
      dependsOn: []
      acceptanceCriteria:
        - Verifiable subtask result
      verification:
        - Test or check proving completion
  rollout: []
```

Keep empty list fields as `[]` and keep the mapping proportional to the ticket.
For a read-only request, return it without editing files. When the user asks to
update or prepare the ticket, replace only the top-level `plan` mapping in the
existing YAML ticket. Preserve `schemaVersion`, `ticket`, `impact`, and any
unrelated fields, then parse the resulting YAML to verify its syntax. Never
create a separate plan document.

## Boundaries

- Do not invent missing requirements or silently resolve open product decisions.
- Do not create a second ticket or a separate plan artifact.
- Do not modify production code or mark subtasks complete.
- Do not change ticket status, close the ticket, or broaden its scope unless the
  user separately requests that action.
