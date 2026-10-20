# Codex Skills

Personal Codex skills shared across repositories.

## Skills

- `change-impact-analysis`: Analyze a Linear issue's codebase impact and maintain its `Impact` section.
- `engineering-ticket`: Create or refine a Linear issue before code changes.
- `implementation-plan`: Turn a Linear issue and its `Impact` section into an executable `Plan`.
- `keep-it-simple`: Keep code, documentation, and other writing simple, efficient, and minimal.
- `project-overview`: Plan a project and maintain its Markdown architecture, libraries, and workflows overview.
- `ponytail`: Prefer the smallest working implementation using YAGNI, existing code, standard-library, and native-platform solutions.
- `ponytail-review`: Review a diff specifically for over-engineering.
- `ponytail-audit`: Audit a repository for unnecessary complexity.
- `ponytail-debt`: Collect deferred `ponytail:` shortcuts into a debt ledger.
- `ponytail-gain`: Show Ponytail's benchmark impact.
- `ponytail-help`: Show Ponytail modes and commands.

## Ticket workflow

One code change uses one Linear issue as its source of truth. Each workflow
skill owns one Markdown section in that issue's description:

```markdown
## Ticket
## Impact
## Plan
```

The skills preserve sections owned by the other workflow stages and never
create repository-local ticket, impact, or plan files. Linear write access is
required to persist changes; without it, the skills return an unsaved draft.
New issues are created in `Todo`, or in `Backlog` when explicitly requested.
Whenever a workflow edits an existing issue, it sets that issue's status to
`In Progress`. Read-only requests do not change the issue.

Every engineering ticket belongs to the correct epic. The ticket workflow uses
an existing matching epic when available. If none exists, it proposes an epic
and asks for confirmation before creating it and associating the ticket.

## Use as repository skills

Add this repository as a submodule at the Codex repository-skill path:

```sh
git submodule add <repository-url> .agents/skills
git submodule update --init --recursive
```

Each skill can also be installed individually from this repository.
