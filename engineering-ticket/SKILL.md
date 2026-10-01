---
name: engineering-ticket
description: >
  Create or refine one repository-local Markdown epic or engineering ticket.
  Use to capture a product outcome or one proposed change before impact analysis
  or planning. Do not analyze implementation impact, plan work, or modify code.
---

# Engineering Ticket

Create the smallest complete Markdown source of truth for the requested work.

## Workflow

1. Read and follow the repository's ticket conventions, especially its ticket README.
2. Create an epic only for a shared product outcome that requires multiple independently
   verifiable tickets. Otherwise create a ticket.
3. Refine an existing artifact for the same work instead of duplicating it.
4. Follow repository location, naming, ID, status, and Markdown heading conventions.
   Without a convention, use `docs/tickets/<ID>-<title-slug>.md` for tickets and
   `docs/tickets/epics/<ID>-<title-slug>.md` for epics.
5. Use the supplied or repository-derived ID. Ask when no stable ID can be determined.
6. Capture only context, outcome, scope, observable success or acceptance criteria,
   constraints, dependencies, and open product questions.
7. Separate known facts from assumptions. Do not guess implementation or resolve unclear
   product behavior.
8. Write or update exactly one Markdown artifact and check its structure.

## Fallback ticket structure

```markdown
# PROJECT-123: Short descriptive title

Status: proposed
Epic: EPIC-001

## Context
## Goal
## Scope
## Acceptance criteria
## Constraints
## Exclusions
## Open questions
```

Omit `Epic:` for standalone tickets and omit empty optional sections. Impact analysis and
implementation planning add their own sections later.

## Fallback epic structure

```markdown
# EPIC-001: Short product outcome

Status: proposed

## Context
## Goal
## Scope
## Success criteria
## Tickets
## Exclusions
## Open questions
```

Do not add affected code, architecture, implementation subtasks, or sequencing unless the
repository convention requires them. Do not create external issues, change status, or modify
production code without a separate request.
