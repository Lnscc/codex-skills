---
name: work-orchestrator
description: >
  Decompose complex work into dependency-aware agent assignments, coordinate
  parallel execution, and integrate verified results. Use when the user
  explicitly asks to distribute work, orchestrate subagents, review an
  execution split, or prepare a delegation plan. Do not use for small tasks
  that are faster and safer for one agent to complete directly.
---

# Work Orchestrator

Coordinate the smallest useful team while keeping scope, ownership, and final
quality under the orchestrator's control.

## Select the mode

- **Plan only**: When the user asks for a delegation plan, return the task graph
  and work packets without spawning agents or mutating artifacts.
- **Execute**: When the user asks to distribute or carry out the work, delegate
  suitable packets, integrate their results, and verify the combined outcome.
- **Review**: When the user supplies an existing split, identify missing work,
  unsafe dependencies, overlapping ownership, and unnecessary delegation.
  Do not execute it unless requested.

If the requested mode is clear, proceed without asking. If delegation has no
material benefit, complete the task directly in execute mode or recommend a
single-agent plan in the other modes, with a brief reason.

## Decide what to delegate

Delegate only when at least two substantial work packets can progress
independently or when a focused specialist pass materially improves confidence.
Prefer fewer agents and reserve capacity for the orchestrator. Do not delegate
the final integration decision, authorization decisions, or the only task on
the critical path.

Before delegation:

1. Read applicable repository instructions and inspect current state.
2. Define the desired outcome, acceptance criteria, constraints, and authorized
   side effects.
3. Split work by concrete deliverable and dependency, not by vague role.
4. Mark packets as parallel, sequential, or blocked.
5. Give writable packets disjoint ownership. Multiple agents may inspect the
   same material, but they must not concurrently edit the same files or shared
   mutable state.

## Create work packets

Every delegated packet must state:

```text
Objective:
Deliverable:
Owned scope:
Relevant inputs:
Constraints and exclusions:
Acceptance checks:
Dependencies:
Report back with:
```

Include only the context needed for that packet. Tell agents to preserve
unrelated work, report assumptions and blockers, and identify changed paths and
verification evidence. Do not give two agents duplicate implementation work
unless the user requested independent alternatives or review.

## Coordinate execution

1. Start independent packets together within the available concurrency limit.
2. Keep dependency-bound packets idle until their prerequisites are satisfied.
3. Use concise status checks; do not repeatedly poll or relay unchanged state.
4. Inspect each result against its packet before accepting it. Treat a worker's
   completion claim as evidence to verify, not as final validation.
5. Resolve integration conflicts centrally. Reassign or retry only with a
   narrower corrected packet and a clear stopping condition.
6. Run the narrowest sufficient checks for the combined result.
7. Report the integrated outcome, verification evidence, unresolved risks, and
   any work that was not completed.

When collaboration tools are unavailable, preserve the same task graph and
either perform the work directly or return an actionable plan, depending on the
requested mode. Never imply that delegation occurred when it did not.

## Boundaries

- Delegation does not expand the user's request, permissions, or authorized
  side effects. Each agent inherits the same boundaries.
- Do not create agents merely to restate context, supervise other agents, or
  split trivial work.
- Do not allow workers to commit, push, merge, release, deploy, contact people,
  or mutate external systems unless the user authorized that action.
- Preserve user-owned and unrelated working-tree changes.
- Ask for direction when a product or scope decision would materially change
  the requested outcome; do not settle it by majority vote among agents.
- The orchestrator remains responsible for the final answer and must distinguish
  verified results from assumptions, skipped checks, and worker reports.
