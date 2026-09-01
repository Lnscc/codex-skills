# Change Impact Report v1

Use this format when the user requests a complete report, a saved artifact, or
structured output. Omit inapplicable optional sections rather than filling them
with boilerplate. Preserve the user's requested file format when one is given.

## Markdown structure

```markdown
# Change impact: <short change name>

## Ticket
- ID: ...
- Source: ...
- Revision: ...

## Executive summary
<blast radius, central dependency path, and highest risk>

## Analysis basis
- Relevant ticket requirements: ...
- Technical assumptions: ...
- Ticket issues or scope questions: ...

## Impact map
| Scope | Confidence | Location | Reason | Expected change |
|---|---|---|---|---|
| direct | confirmed | `path` — `symbol` | ... | ... |

## Interface and data changes
### APIs and events
...
### Data models and migrations
...

## Verification and operations
- Tests: ...
- Observability: ...
- Configuration/deployment: ...

## Risks and decisions
### Risks
...
### Open decisions
...
### Unknowns
...

## Dependency paths
`entry point` → `service` → `persistence`
```

## Structured record

When machine-readable output is useful, append or save this YAML shape. This is
an analysis record, not yet a promise of compatibility with a particular viewer.

```yaml
schemaVersion: 1
kind: change-impact-analysis
ticket:
  id: string
  title: string
  source: string
  revision: string | null
analysis:
  summary: string
  requirementRefs: [string]
  technicalAssumptions: [string]
  ticketIssues: [string]
impacts:
  - scope: direct | indirect | conditional
    confidence: confirmed | inferred | unknown
    location:
      path: string
      symbol: string | null
    reason: string
    expectedChange: string
interfaces:
  - kind: api | event | command | configuration
    name: string
    change: string
    compatibility: string | null
data:
  - store: string
    structure: string
    change: string
    migration: string | null
verification:
  tests: [string]
  operations: [string]
risks:
  - description: string
    mitigation: string | null
decisions:
  open: [string]
unknowns: [string]
dependencyPaths:
  - [string]
```

The ticket reference identifies the authoritative requirements; the report does
not replace them. Every `confirmed` impact must have a repository location or
another explicit piece of evidence. Use `unknown` when the available repository
state cannot answer the question; do not turn absence of evidence into a
negative finding.
