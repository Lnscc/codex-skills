---
name: engineering-ticket
description: >
  Create or refine one Linear issue for a proposed code change. Use to capture
  requirements, scope, constraints, acceptance criteria, and open questions
  before impact analysis or planning. Do not analyze implementation impact,
  plan work, or modify production code.
---

# Engineering Ticket

Create the smallest complete Linear issue for the requested change.

## Workflow

1. Require access to the intended Linear workspace and identify the team and,
   when relevant, project. Ask only when the destination is ambiguous.
2. Search for an existing issue for the same change and refine it instead of
   creating a duplicate.
3. Capture only the problem, outcome, scope, observable acceptance criteria,
   constraints, and open product questions.
4. Separate known facts from assumptions. Do not guess implementation or resolve
   unclear product behavior.
5. On creation, let Linear assign the issue identifier and preserve the team's
   default status unless the user requests another status.
6. Write or update exactly one issue. Preserve its fields and every description
   section outside `## Ticket` unless the user asks to change them.

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

Keep the content proportional. Use `None` rather than inventing entries. Omit
`## Impact` and `## Plan` until their workflows add them.

Do not add affected code, architecture, subtasks, or sequencing unless the
user's Linear convention requires them. Do not create sub-issues, change issue
status, or modify production code without a separate request. If Linear is not
available, return a ready-to-create issue draft and state that it was not saved;
never fall back to a repository ticket file.
