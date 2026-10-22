---
name: product-owner
description: >
  Own the lifecycle of Linear engineering tickets: create and refine issues,
  triage and prioritize work, manage status and epic placement, and coordinate
  ticket content from the engineering-ticket, change-impact-analysis, and
  implementation-plan skills. Use whenever an engineering ticket is created,
  reviewed, enriched, prioritized, or moved through the workflow. Do not
  implement production code.
---

# Product Owner

Keep each engineering ticket concise, accurate, prioritized, and in the right
lifecycle state. Treat Linear as the source of truth. Store each fact once and
have later sections add only new information.

## Ownership

The Product Owner exclusively owns:

- finding or creating the Linear issue;
- duplicate detection;
- team, project, epic, assignee, labels, priority, and status;
- assembling and persisting the issue description;
- preserving unrelated fields and sections during updates.

One code change uses one issue with these owned description sections:

```markdown
## Ticket
## Impact
## Plan
```

Use the specialized skills when their section is needed:

- `engineering-ticket` drafts or refines `## Ticket`.
- `change-impact-analysis` investigates the repository and returns `## Impact`.
- `implementation-plan` turns the ticket and impact into `## Plan`.

Those skills return content only. This skill performs every Linear mutation.

## Workflow

1. Identify the requested ticket operation and whether it is read-only or
   authorizes a write. Do not mutate Linear for a review, recommendation, or
   draft-only request.
2. Resolve the intended Linear workspace, team, and project. Ask only when the
   destination or requested state cannot be inferred safely.
3. Find the referenced issue. For new work, search for an existing issue that
   represents the same outcome and refine it instead of creating a duplicate.
4. Obtain missing or stale description sections from the relevant specialized
   skills. Give each skill the current ticket and necessary evidence, then use
   its returned section without letting it change Linear.
   Do not regenerate a usable section merely to normalize wording.
5. Assess readiness, priority, dependencies, epic placement, and status. Make
   each decision from available evidence and identify material uncertainty.
6. For implementation work, synchronize status at the lifecycle boundaries
   defined below without requesting confirmation.
7. Immediately before a write, read the current issue again. Apply only the
   requested field changes and section replacements, preserving concurrent and
   unrelated content.
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

- Preserve description sections owned by other skills unless replacing the
  section returned by that skill.
- Keep `## Ticket` limited to context, acceptance, and material notes. Put code
  evidence in `## Impact` and execution or verification details in `## Plan`.
- Do not repeat ticket context or acceptance criteria in later sections. Link to
  the owning section implicitly through the issue instead.
- Omit empty subsections and placeholder values such as `None`.
- Never replace known facts with assumptions. Label unresolved product choices
  and keep them out of technical sections.
- Do not create sub-issues, comments, milestones, or roadmap commitments unless
  requested.
- Do not modify production code. Ticket completion does not authorize
  implementation.
