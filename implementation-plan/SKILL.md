---
name: implementation-plan
description: >
  Turn an existing engineering ticket and its change-impact analysis into an
  ordered, executable implementation plan with scoped subtasks, dependencies,
  acceptance criteria, and verification. Use when the user asks how a ticket
  should be implemented, wants work broken down, or needs a plan before coding.
  The plan is returned as a section for that same ticket and is written there
  only when requested. This skill plans work; it does not create requirements,
  analyze architectural impact from scratch, or modify production code.
---

# Implementation Plan

Translate the ticket's accepted requirements and evidence-backed impact into the
smallest complete sequence of implementation work. The ticket remains the source
of truth; the plan must not quietly expand or reinterpret it.

## Planning

1. Locate and read the complete ticket. Require a `## Change impact` section or
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

Return a `## Implementation plan` section containing:

- a short approach summary;
- assumptions, blockers, and decisions still required;
- ordered subtasks with stable local IDs;
- explicit `Depends on` relationships where ordering matters;
- acceptance criteria and verification for each subtask;
- rollout or migration notes only when relevant.

Use this shape unless the repository already defines one:

```markdown
## Implementation plan

### Approach
...

### Blockers and decisions
- ...

### Subtasks

#### PLAN-1: <Outcome>
- Status: planned
- Depends on: none
- Affected areas: ...
- Acceptance criteria:
  - ...
- Verification:
  - ...
```

Keep the section proportional to the ticket. For a read-only request, return it
without editing files. When the user asks to update or prepare the ticket, add or
replace this section in the existing ticket instead of creating a separate plan
document. Preserve all requirements, impact findings, and unrelated content.

## Boundaries

- Do not invent missing requirements or silently resolve open product decisions.
- Do not create a second ticket or a separate plan artifact.
- Do not modify production code or mark subtasks complete.
- Do not change ticket status, close the ticket, or broaden its scope unless the
  user separately requests that action.
