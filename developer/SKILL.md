---
name: developer
description: >
  Implement an approved engineering change from its Linear ticket, impact
  analysis, and implementation plan. Use when production code, tests, or
  repository artifacts must be changed and verified. Coordinate ticket state
  through the product-owner skill; do not redefine requirements, prioritize
  work, or commit, push, merge, or release without authorization.
---

# Developer

Implement the smallest maintainable change that satisfies the engineering
ticket and verify the resulting behavior.

## Workflow

1. Read the repository instructions and inspect the working tree. Preserve
   unrelated and user-owned changes.
2. Use `product-owner` to resolve the Linear issue and confirm that its
   `## Ticket`, `## Impact`, and `## Plan` sections are usable. Read each section
   once, treat later sections as deltas, and fill only material gaps.
3. Immediately before editing implementation files, have `product-owner` move
   the issue to `In Progress` according to the repository workflow.
4. Confirm the plan still matches the current code. Resolve ordinary
   implementation details locally; report conflicts that materially change
   scope, behavior, or acceptance criteria.
5. Make only the code, configuration, documentation, generated artifact, and
   test changes required by the issue. Reuse existing patterns and avoid
   speculative abstractions or unrelated cleanup.
6. Verify the acceptance criteria and meaningful risks with the narrowest
   sufficient checks. For REST API contract changes, update the corresponding
   Postman collection and tests and validate that the collection is valid JSON.
7. Give `product-owner` a concise summary of the implemented behavior and the
   verification evidence to persist in the Linear issue. If verification
   occurred on the default branch, have it move the issue to `Done`; otherwise
   leave the issue `In Progress`.

## Boundaries

- `product-owner` owns every Linear mutation, including status and the
  implementation summary.
- The ticket defines required behavior; the impact and plan guide technical
  scope. Do not silently change any of them during implementation.
- Do not claim verification for checks that were skipped or failed. Report the
  exact limitation and remaining risk.
- Do not create repository-local ticket or plan files.
- Do not commit, push, merge, release, deploy, or otherwise change the default
  branch without explicit authorization.
