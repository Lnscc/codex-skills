---
name: engineering-ticket
description: >
  Draft or refine the Ticket section for one proposed engineering change. Use
  to capture requirements, scope, constraints, acceptance criteria, and open
  questions before impact analysis or planning. Return content to the Product
  Owner; do not create or modify Linear issues, analyze implementation impact,
  plan work, or modify production code.
---

# Engineering Ticket

Draft the smallest complete `## Ticket` section for the requested change.

## Workflow

1. Read the proposed change and, when supplied, the current issue content.
2. Capture only the problem, outcome, scope, observable acceptance criteria,
   constraints, and open product questions.
3. Separate known facts from assumptions. Do not guess implementation or resolve
   unclear product behavior.
4. Preserve valid existing requirements and tighten only the requested content.
5. Return a concise outcome-oriented title suggestion with the section when a
   new title or issue is needed.

## Issue format

Use a concise outcome-oriented issue title. Place the following Markdown section
in the description:

```markdown
## Ticket

### Problem
Why the change is needed.

### Goal
Observable outcome without implementation details.

### Scope

Included:
- Required outcome

Excluded:
- Explicit non-goal

### Acceptance criteria
- [ ] Observable or verifiable result

### Constraints
- None

### Open questions
- None
```

Keep the content proportional. Use `None` rather than inventing entries. Do not
produce `## Impact` or `## Plan`.

Do not add affected code, architecture, subtasks, or sequencing unless the
user's issue format explicitly requires them. Return the proposed title and
`## Ticket` section without writing to Linear or a repository file. The
`product-owner` skill owns issue lookup, creation, description updates, epic
placement, priority, status, and all other Linear fields.
