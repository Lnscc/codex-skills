---
name: local-ticket-workflow
description: Find and process repository-local tickets stored under docs/tickets. Use whenever the user provides a ticket identifier such as ART-003, mentions a local ticket, or asks to inspect, explain, implement, test, or complete a ticket that may be documented in the current codebase.
---

# Local ticket workflow

When given a ticket identifier:

1. Search `docs/tickets` recursively for the identifier. Prefer an exact filename match, then search file contents with `rg`.
2. Read the complete matching ticket before inspecting or modifying code.
3. Treat the local ticket as the primary source of requirements and acceptance criteria.
4. Inspect the relevant production code and tests.
5. Determine whether the user requests information, diagnosis, or implementation. Do not implement changes for a read-only request.
6. For implementation requests, implement the smallest complete change and run relevant tests.
7. Report the result against the ticket's acceptance criteria, including tests and remaining uncertainties.

When closing a ticket:

1. Change its status and move it to the completed-ticket directory only after the user explicitly confirms the status change.
2. Inspect the remaining open tickets and their dependency context after the closure.
3. Name the actionable tickets that are reasonable next candidates.
4. Recommend exactly one preferred next ticket and briefly explain why it should come first.
5. Mention material dependencies, blockers, or sequencing constraints.

Do not query an external issue tracker when a matching local ticket exists. Only use an external tracker when no local ticket exists or the user explicitly requests it.

If exactly one ticket matches, proceed without asking where it is. If multiple tickets match, explain the ambiguity. If none match, report that no local ticket was found.

Do not change ticket status or move the ticket file unless explicitly requested.
