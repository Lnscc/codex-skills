# Codex Skills

Personal Codex skills shared across repositories.

## Skills

- `change-impact-analysis`: Analyze a Markdown ticket's codebase impact and add its impact section.
- `engineering-ticket`: Create or refine a repository-local Markdown epic or ticket.
- `implementation-plan`: Turn a Markdown ticket and its impact section into an executable plan.
- `keep-it-simple`: Keep code, documentation, and other writing simple, efficient, and minimal.
- `project-overview`: Plan a project and maintain its Markdown architecture, libraries, and workflows overview.
- `ponytail`: Prefer the smallest working implementation using YAGNI, existing code, standard-library, and native-platform solutions.
- `ponytail-review`: Review a diff specifically for over-engineering.
- `ponytail-audit`: Audit a repository for unnecessary complexity.
- `ponytail-debt`: Collect deferred `ponytail:` shortcuts into a debt ledger.
- `ponytail-gain`: Show Ponytail's benchmark impact.
- `ponytail-help`: Show Ponytail modes and commands.

## Ticket workflow

One code change uses one repository-local Markdown ticket. A larger product outcome may use one
epic with multiple tickets. Each workflow skill owns one part of the same ticket:

```text
Ticket requirements         # engineering-ticket
## Impact analysis          # change-impact-analysis
## Implementation plan     # implementation-plan
```

The skills preserve sections owned by the other workflow stages and never create parallel impact
or plan files.

## Use as repository skills

Add this repository as a submodule at the Codex repository-skill path:

```sh
git submodule add <repository-url> .agents/skills
git submodule update --init --recursive
```

Each skill can also be installed individually from this repository.
