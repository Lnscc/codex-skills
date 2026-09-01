# Codex Skills

Personal Codex skills shared across repositories.

## Skills

- `change-impact-analysis`: Analyze a ticket's codebase impact and prepare its impact section.
- `engineering-ticket`: Create or refine a repository-local source ticket before code changes.
- `ponytail`: Prefer the smallest working implementation using YAGNI, existing code, standard-library, and native-platform solutions.
- `ponytail-review`: Review a diff specifically for over-engineering.
- `ponytail-audit`: Audit a repository for unnecessary complexity.
- `ponytail-debt`: Collect deferred `ponytail:` shortcuts into a debt ledger.
- `ponytail-gain`: Show Ponytail's benchmark impact.
- `ponytail-help`: Show Ponytail modes and commands.

## Use as repository skills

Add this repository as a submodule at the Codex repository-skill path:

```sh
git submodule add <repository-url> .agents/skills
git submodule update --init --recursive
```

Each skill can also be installed individually from this repository.
