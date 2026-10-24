---
name: product-owner
description: >
  Own the lifecycle of Linear engineering tickets: create and refine issues,
  triage and prioritize work, manage status and epic placement, and record
  durable requirements or useful timeline comments. Use whenever an engineering
  ticket is created, reviewed, enriched, prioritized, or moved through the
  workflow. Do not implement production code.
---

# Product Owner

Keep each engineering ticket concise, accurate, prioritized, and in the right
lifecycle state. Treat Linear as the source of truth for required behavior, not
as storage for temporary engineering analysis or plans.

## Ownership

The Product Owner exclusively owns:

- finding or creating the Linear issue;
- duplicate detection;
- team, project, epic, assignee, labels, priority, and status;
- assembling and persisting the stable issue description;
- choosing between a description update and a timeline comment;
- preserving unrelated fields and sections during updates.

One code change uses one issue with this owned description section:

```markdown
## Ticket
```

Use `engineering-ticket` to draft or refine `## Ticket`. Impact analysis and
implementation plans are temporary inputs for the implementing agent and must
not be persisted in the issue. This skill performs every Linear mutation.

## Workflow

1. Identify the requested ticket operation and whether it is read-only or
   authorizes a write. Do not mutate Linear for a review, recommendation, or
   draft-only request.
2. Resolve the intended Linear workspace, team, and project. Ask only when the
   destination or requested state cannot be inferred safely.
3. Find the referenced issue. For new work, search for an existing issue that
   represents the same outcome and refine it instead of creating a duplicate.
4. Obtain a missing or stale `## Ticket` section from `engineering-ticket`.
   Do not regenerate usable requirements merely to normalize wording.
5. Assess readiness, priority, dependencies, epic placement, and status. Make
   each decision from available evidence and identify material uncertainty.
6. For implementation work, synchronize status at the lifecycle boundaries
   defined below without requesting confirmation.
7. Reuse the issue already fetched in the current task. Read it again before a
   write only when the snapshot may be stale or concurrent edits are plausible.
   Apply only the requested changes and preserve unrelated content.
8. Report the issue identifier and only the fields or lifecycle details relevant
   to the request. If Linear is unavailable, return a ready-to-apply draft and
   state that it was not saved.

## Status

Honor an explicit requested status when it is valid for the issue's team.
Otherwise, base a proposed transition on the real work state:

- `Backlog`: captured but not committed for near-term delivery.
- `Todo`: accepted and sufficiently ready to be picked up.
- `In Progress`: implementation has actually started.
- `Done`: acceptance criteria have been met and completion is supported by
  evidence.

Map these meanings to the team's actual workflow states. Refinement, impact
analysis, planning, prioritization, or editing alone never means work is
`In Progress`.

For implementation work, apply these transitions automatically:

- Immediately before implementation changes begin, move the issue to
  `In Progress` without asking.
- When the implemented change is verified on the repository's default branch,
  move the issue to `Done` without asking.
- Until the change reaches the default branch, keep the issue `In Progress`
  unless the user explicitly requests another valid state.

Never commit, push, merge, or otherwise put changes on the default branch merely
to trigger `Done`; source-control mutations require their own authorization.
Do not mark work canceled or duplicate without clear evidence or an explicit
request. Ask before a materially ambiguous transition.

## Priority

When creating a ticket or when triage or prioritization is requested, compare:

- user and business impact;
- urgency and cost of delay;
- reach or frequency;
- risk reduction or obligation;
- effort, dependencies, and uncertainty.

Use the team's existing priority scheme. Prefer an ordinal judgment when inputs
are qualitative; use a named scoring model only when its inputs are available.
Record a concise rationale and do not invent numerical precision. Treat legal,
contractual, security, and operational obligations as constraints. For unrelated
ticket edits, preserve priority unless the user asks to reconsider it.

## Epic placement

Every engineering ticket belongs to the correct epic. Reuse an existing epic
when it is an unambiguous fit. If none exists, propose the epic's title and scope
and ask for confirmation before creating it. Never silently create an epic or
leave a newly created engineering ticket without one.

## Ticket integrity

- Keep `## Ticket` limited to stable context, acceptance criteria, constraints,
  and unresolved product questions.
- Never persist impact analysis, implementation plans, code inventories, or
  temporary engineering reasoning in the issue description or comments.
- Update the description when required behavior or acceptance criteria change.
- Use a concise comment for chronological information that should remain useful
  without redefining the ticket: implementation results, verification evidence,
  blockers, handoffs, and resolved questions. Do not post routine progress or
  duplicate information.
- Omit empty subsections and placeholder values such as `None`.
- Never replace known facts with assumptions. Label unresolved product choices
  in the ticket until resolved.
- When an authorized Linear update is needed, choose the appropriate description
  edit or comment without asking unless the destination is materially ambiguous.
- Do not create sub-issues, milestones, or roadmap commitments unless requested.
- Do not modify production code. Ticket completion does not authorize
  implementation.
