---
name: engineering-ticket
description: >
  Draft or refine the description for one proposed engineering change. Use to
  capture requirements, scope, constraints, acceptance criteria, and open
  questions before impact analysis or planning. Return content to the Product
  Owner; do not create or modify Linear issues, analyze implementation impact,
  plan work, or modify production code.
---

# Engineering Ticket

Draft the smallest issue description that makes the requested outcome
unambiguous and testable.

## Workflow

1. Read the proposed change and, when supplied, the current issue content.
2. Summarize the problem and desired outcome in one short context paragraph.
3. Add only observable acceptance criteria that are not already implied by a
   broader criterion.
4. Add constraints, exclusions, or open product questions only when they change
   implementation or acceptance. Omit empty headings.
5. Separate known facts from assumptions. Do not guess implementation or resolve
   unclear product behavior.
6. Preserve valid existing requirements, but remove repetition and stale
   scaffolding when refining a ticket.
7. Return a concise outcome-oriented title suggestion with the description when a
   new title or issue is needed.

## Issue format

Use a concise outcome-oriented issue title. Use this Markdown directly as the
description:

```markdown
Short context: current problem and desired outcome.

### Acceptance
- [ ] Observable or verifiable result

### Notes
- Constraint, explicit exclusion, or open question only when relevant
```

Keep the context to one paragraph and prefer a small set of outcome-level
criteria. Do not create separate problem, goal, scope, or manual-test sections
when they would restate the same behavior. Omit `### Notes` when unused; never
write placeholder values such as `None`.

Do not add affected code, architecture, verification procedure, subtasks, or
sequencing. Those belong to impact analysis or planning. Return the proposed
title and description without writing to Linear or a repository file. The
`product-owner` skill owns all Linear operations and fields.
