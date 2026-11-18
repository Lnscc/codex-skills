---
name: work-orchestrator
description: >
  Decompose complex work into dependency-aware agent assignments, coordinate
  parallel execution, and integrate verified results. Use proactively when
  substantial independent parts of an authorized task can progress in parallel,
  or when the user asks to orchestrate subagents, review an execution split,
  or prepare a delegation plan. Keep small or tightly dependent tasks with one agent.
---

# Work Orchestrator

Coordinate the smallest useful team while keeping scope, ownership, and final
quality under the orchestrator's control.

## Automatic use

For an execution request, assess whether independent work can usefully run in
parallel. When it can, use the available collaboration tools to spawn subagents
without asking for separate delegation approval. This skill explicitly calls
for parallel agent work in that case; the original task still defines scope
and authorized side effects. A request to create or edit this skill alone does
not require spawning agents.

Use `spawn_agent` for subtasks within the current chat, not user-facing chat
creation tools. Give workers bounded assignments and continue useful work
yourself while they run. Workers should report back rather than recursively
delegate unless their assignment explicitly calls for further delegation.

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
When the skill applies to a concrete execution task and no mode is specified,
use Execute. Requests to plan, split, or review still select their named mode.

## Decide what to delegate

Delegate only when at least two substantial work packets can progress
independently or when a focused specialist pass materially improves confidence.
Prefer fewer agents and reserve capacity for the orchestrator. Do not delegate
the final integration decision, authorization decisions, or the only task on
the critical path.

Before spawning, state in one sentence why delegation will materially reduce
elapsed time or improve confidence after accounting for context transfer,
coordination, and duplicate verification. If that benefit is unclear, do the
work with one agent.

Before delegation:

1. Read applicable repository instructions and inspect current state.
2. Define the desired outcome, acceptance criteria, constraints, and authorized
   side effects.
3. Split work by concrete deliverable and dependency, not by vague role.
4. Mark packets as parallel, sequential, or blocked.
5. Give writable packets disjoint ownership. Multiple agents may inspect the
   same material, but they must not concurrently edit the same files or shared
   mutable state.
6. Assign every check to one owner. Workers own packet-local checks; the
   orchestrator owns combined builds, integration tests, and final validation.

## Create work packets

Use this compact template and omit empty or self-evident fields:

```text
Objective:
Deliverable:
Owned scope:
Relevant inputs:
Constraints and exclusions:
Acceptance checks:
Verification owner:
Dependencies:
Report back with:
```

Keep each entry brief. Include established findings so workers do not repeat
discovery. Tell agents to preserve unrelated work, report assumptions and
blockers, and identify changed paths and verification evidence. Do not give two
agents duplicate implementation or verification work unless the user requested
independent alternatives or review.

## Coordinate execution

1. Start independent packets together within the available concurrency limit.
2. Keep dependency-bound packets idle until their prerequisites are satisfied.
3. Use concise status checks; do not repeatedly poll or relay unchanged state.
   Do not run shared build or test commands concurrently.
4. Inspect each result against its packet before accepting it. Treat a worker's
   completion claim as evidence to verify, not as final validation.
5. Resolve integration conflicts centrally. Reassign or retry only with a
   narrower corrected packet and a clear stopping condition.
6. If a command is unexpectedly silent for 30 seconds and no child process is
   active, stop it. Diagnose once and retry only when the retry changes a
   relevant condition; otherwise report the blocker to the orchestrator.
7. Run the narrowest sufficient checks for the combined result.
8. Report the integrated outcome, verification evidence, unresolved risks, and
   any work that was not completed.

## Review and verification

- Review the integrated diff for correctness, scope, compatibility, test
  coverage, and preservation of unrelated work before accepting it.
- For high-risk or cross-cutting code, use an independent read-only review pass
  when delegation is available and the added cost is proportionate. Typical
  triggers include security, authorization, schema or data migrations,
  concurrency, and public contracts. Give the reviewer requirements and the
  diff, but not the implementer's conclusions or proposed findings.
- Prefer repository-local checks. Use external CI, remote test environments, or
  third-party validation only when they provide distinct evidence and are
  available within the task's authorization, cost, and side-effect boundaries.
  Never push, publish, or trigger a state-changing external run merely to test.
- Report which local and external checks ran, which were skipped, and why.

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
