---
name: engineering-ticket
description: >
  Create or refine a repository-local engineering ticket before code changes.
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
   IDs, statuses, and templates. Follow an established convention when one
   exists; otherwise use `docs/tickets/<TICKET-ID>-<title-slug>.md`.
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
6. Write or update exactly one ticket document and report its path plus any
   unresolved questions.

## Ticket shape

Adapt headings to an existing repository template. When no template exists, use:

```markdown
# <TICKET-ID>: <Title>

Status: proposed

## Problem
<Why this change is needed and the relevant current behavior.>

## Goal
<The observable outcome, without prescribing implementation.>

## Scope

### Included
- ...

### Excluded
- ...

## Acceptance criteria
- ...

## Constraints
- ...

## Open questions
- ...
```

Omit empty optional sections instead of adding placeholders. Acceptance criteria
must describe externally observable or verifiable outcomes, not implementation
steps such as changing a particular class.

## Boundaries

- Do not inspect the codebase to determine architectural impact; that belongs to
  change-impact analysis after the ticket exists.
- Do not add affected files, modules, API changes, database changes, subtasks,
  or implementation sequencing to the ticket unless the repository's existing
  ticket template explicitly requires them.
- Later analysis and planning workflows may append their own sections to this
  same ticket. Do not create parallel ticket documents for those results.
- Do not create an external tracker issue unless the user explicitly asks for
  one.
- Do not change ticket status, close or move a ticket, or modify production code
  unless the user separately requests that action.
