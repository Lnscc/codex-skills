---
name: suggest-next-ticket
description: Recommend the next repository-local ticket to work on, wait for the user's selection, rename the current Codex task, and immediately begin implementing the selected ticket. Use when the user asks which ticket, issue, or work item should be next, and continue using it when the user accepts the recommendation or chooses a different ticket in a follow-up message.
---

# Suggest Next Ticket

Recommend one actionable local ticket, let the user decide, rename the current Codex task to match the chosen ticket, then immediately implement it.

## Workflow

1. Inspect repository instructions such as `AGENTS.md` and the ticket directory, normally `docs/tickets`.
2. Use an available repository-local ticket workflow skill when one exists. Read ticket contents and relevant dependency or planning context; do not rank tickets from filenames alone.
3. Exclude completed, blocked, superseded, or dependency-gated tickets when the repository evidence supports doing so. Do not change ticket files or statuses during recommendation.
4. Recommend exactly one ticket. State its identifier, title, and a concise reason it is the best next choice. Mention a material dependency or uncertainty when relevant.
5. Ask the user to confirm that ticket or name another one. Do not rename the task yet.
6. Preserve the pending recommendation across the user's next message. Treat an unambiguous acceptance such as "ja", "okay", "mach das", or "nimm das" as selecting the recommended ticket. Treat a ticket identifier or clearly named alternative as overriding it. Ask a concise clarification only if the choice remains ambiguous.
7. Once a ticket is selected, find and call the Codex thread-title tool, normally `set_thread_title`, for the current task. Use the title format `<TICKET-ID>: <short ticket title>`. Keep it concise and do not include workflow prefixes such as "Implement" or "Working on".
8. After the rename attempt, immediately follow the repository-local ticket workflow and begin implementing the selected ticket without asking for another confirmation. A missing or failed title tool does not block implementation.
9. Complete and verify the implementation according to the ticket, repository instructions, and applicable skills. Report the selected ticket, rename result, implementation, tests, and remaining uncertainties.

## Boundaries

- Renaming is authorized only after the user selects a ticket.
- Selecting a ticket authorizes its immediate implementation after the rename attempt.
- Selection does not authorize status changes, moving ticket files, or Git operations.
