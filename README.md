# Codex Skills

Personal Codex skills available across local repositories.

## Skills

- `change-impact-analysis`: Analyze an engineering issue's codebase impact and return its `Impact` section.
- `codex-chat-namer`: Keep a Codex chat title aligned with its current primary goal.
- `developer`: Implement and verify an approved engineering change from its Linear ticket.
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
- `work-orchestrator`: Split complex work into dependency-aware agent assignments, coordinate execution, and verify the integrated result.

## Ticket workflow

One code change uses one concise Linear issue as its source of truth. Each fact
is stored once: requirements in `Ticket`, code evidence in `Impact`, and
execution details in `Plan`.

```markdown
## Ticket
## Impact
## Plan
```

The specialist skills return only their section and omit empty headings and
repeated context. They never mutate Linear or create repository-local ticket,
impact, or plan files. The `product-owner` skill assembles their output,
preserves unrelated content, and owns all Linear reads and writes. Without
Linear access, it returns an unsaved draft.

The Product Owner manages status according to the actual work state; editing,
refinement, impact analysis, and planning do not by themselves move an issue to
`In Progress`. It also owns prioritization and ensures every engineering ticket
belongs to the correct epic. If no matching epic exists, it proposes one and
asks for confirmation before creating it.

## Use as personal global skills

Codex discovers personal skills in `$HOME/.agents/skills`. Use this repository as
that directory, or link that directory to the repository checkout. For example,
on Windows PowerShell, when `$HOME/.agents/skills` does not exist:

```powershell
New-Item -ItemType Directory -Force "$HOME\.agents"
New-Item -ItemType Junction -Path "$HOME\.agents\skills" -Target "<path-to-this-repository>"
```

The repository remains the single versioned source for all personal skills.
