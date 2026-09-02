---
name: engineering-ticket
description: >
  Create or refine one repository-local YAML ticket for a proposed code change.
  Use to capture requirements, scope, constraints, acceptance criteria, and open
  questions before impact analysis or planning. Do not analyze implementation
  impact, plan work, or modify production code.
---

# Engineering Ticket

Create the smallest complete source of truth for the requested change.

## Workflow

1. Follow repository ticket location, naming, ID, status, and schema conventions.
   Without a convention, use `docs/tickets/<TICKET-ID>-<title-slug>.yaml` and
   the fallback schema below.
2. Refine an existing ticket for the same change instead of duplicating it.
3. Use the supplied or repository-derived ID. Ask when no stable ID can be
   determined.
4. Capture only the problem, outcome, scope, observable acceptance criteria,
   constraints, and open product questions.
5. Separate known facts from assumptions. Do not guess implementation or resolve
   unclear product behavior.
6. Write or update exactly one ticket and validate its YAML.

## Fallback schema

```yaml
schemaVersion: 1
ticket:
  id: PROJECT-123
  title: Short descriptive title
  status: proposed
  problem: Why the change is needed
  goal: Observable outcome without implementation details
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

Keep empty lists as `[]`. Omit `impact` and `plan` until their workflows add
them to the same file.

Do not add affected code, architecture, subtasks, or sequencing unless the
repository schema requires them. Do not create external issues, change ticket
status, or modify production code without a separate request.
