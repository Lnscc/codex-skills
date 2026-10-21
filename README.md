# Codex Skills

Personal Codex skills shared across repositories.

## Skills

- `change-impact-analysis`: Analyze an engineering issue's codebase impact and return its `Impact` section.
- `engineering-ticket`: Draft or refine the requirements in an engineering issue's `Ticket` section.
- `implementation-plan`: Turn an issue and its `Impact` section into an executable `Plan` section.
- `keep-it-simple`: Keep code, documentation, and other writing simple, efficient, and minimal.
- `product-owner`: Orchestrate engineering tickets and own their Linear lifecycle, priority, status, and epic placement.
- `project-overview`: Plan a project and maintain its Markdown architecture, libraries, and workflows overview.
- `ponytail`: Prefer the smallest working implementation using YAGNI, existing code, standard-library, and native-platform solutions.
- `ponytail-review`: Review a diff specifically for over-engineering.
- `ponytail-audit`: Audit a repository for unnecessary complexity.
- `ponytail-debt`: Collect deferred `ponytail:` shortcuts into a debt ledger.
- `ponytail-gain`: Show Ponytail's benchmark impact.
- `ponytail-help`: Show Ponytail modes and commands.

## Ticket workflow

One code change uses one Linear issue as its source of truth. The Product Owner
coordinates the workflow and owns all Linear reads and writes. The specialist
skills return one Markdown section each:

```markdown
## Ticket
## Impact
## Plan
```

`engineering-ticket` returns `## Ticket`, `change-impact-analysis` returns
`## Impact`, and `implementation-plan` returns `## Plan`. They never mutate
Linear or create repository-local ticket, impact, or plan files. The
`product-owner` skill assembles their output, preserves unrelated content, and
updates the issue when the user requests a write. Without Linear access, it
returns an unsaved draft.

The Product Owner manages status according to the actual work state; editing,
refinement, impact analysis, and planning do not by themselves move an issue to
`In Progress`. It also owns prioritization and ensures every engineering ticket
belongs to the correct epic. If no matching epic exists, it proposes one and
asks for confirmation before creating it.

## Use as repository skills

Add this repository as a submodule at the Codex repository-skill path:

```sh
git submodule add <repository-url> .agents/skills
git submodule update --init --recursive
```

Each skill can also be installed individually from this repository.
