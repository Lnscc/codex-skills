---
name: engineering-ticket
description: >
  Create or refine a repository-local YAML engineering ticket before code changes.
  Use when the user asks to create a ticket, describes a code change that has no
  ticket yet, or wants requirements, scope, and acceptance criteria made ready
  for later impact analysis and implementation planning. This skill writes the
  ticket document only; it does not analyze the codebase, create an
  implementation plan, or modify production code.
---

# Engineering Ticket

Create the repository-local source of truth for a proposed code change. The
ticket explains the problem, intended outcome, boundaries, and observable
completion criteria without guessing the implementation.

## Workflow

1. Read repository instructions and inspect existing ticket locations, naming,
   IDs, statuses, and schemas. Follow an established YAML convention when one
   exists; otherwise use `docs/tickets/<TICKET-ID>-<title-slug>.yaml` and the
   fallback shape below.
2. Search for an existing ticket that represents the same change. Refine that
   ticket instead of creating a duplicate.
3. Determine the ticket ID from the repository convention or a user-provided
   ID. If no stable convention can be inferred, ask for the ID rather than
   inventing a permanent project identifier.
4. Capture only requirements-level information:
   - title and initial status;
   - problem and relevant current behavior;
   - goal and expected user or system outcome;
   - included and excluded scope;
   - testable acceptance criteria;
   - known constraints;
   - open product questions.
5. Distinguish facts supplied by the user or repository from assumptions. Put
   unresolved product behavior in open questions; do not silently decide it.
6. Write or update exactly one ticket document, parse the resulting YAML to
   verify its syntax, and report its path plus any unresolved questions.

## Ticket shape

Adapt fields to an existing repository schema. When none exists, use:

```yaml
schemaVersion: 1
ticket:
  id: PROJECT-123
  title: Short descriptive title
  status: proposed
  problem: >
    Why this change is needed and the relevant current behavior.
  goal: >
    The observable outcome, without prescribing implementation.
  scope:
    included:
      - Required outcome
    excluded:
      - Explicit non-goal
  acceptanceCriteria:
    - Observable or verifiable result
  constraints: []
  openQuestions: []
```

Keep empty list fields as `[]` so later skills can rely on a stable shape. Omit
`impact` and `plan` until those workflows produce them. Acceptance criteria must
describe observable or verifiable outcomes, not implementation steps such as
changing a particular class.

## Boundaries

- Do not inspect the codebase to determine architectural impact; that belongs to
  change-impact analysis after the ticket exists.
- Do not add affected files, modules, API changes, database changes, subtasks,
  or implementation sequencing to the ticket unless the repository's existing
  ticket template explicitly requires them.
- Later analysis and planning workflows may add top-level `impact` and `plan`
  mappings to this same YAML file. Do not create parallel ticket documents for
  those results.
- Do not create an external tracker issue unless the user explicitly asks for
  one.
- Do not change ticket status, close or move a ticket, or modify production code
  unless the user separately requests that action.
