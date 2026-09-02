---
name: change-impact-analysis
description: >
  Analyze an existing YAML engineering ticket against its codebase and identify its
  architectural blast radius: affected files and modules, dependency paths,
  APIs, data models, migrations, tests, risks, and open decisions. Use when the
  user asks what a ticket touches, what could break, or wants an impact report
  before coding. A diff may provide additional evidence but does not replace
  the ticket. The analysis is returned as an `impact` mapping for that same ticket and is
  written there only when requested. This skill does not create tickets,
  implement changes, or approve designs.
---

# Change Impact Analysis

Produce an evidence-backed map from a versioned engineering ticket to the parts
of the repository that must or may change. The ticket is the source of truth for
the problem, goal, scope, constraints, and acceptance criteria. Optimize for
decision usefulness, not for a long inventory of loosely related files.

## Analysis

1. Locate the ticket and record its ID, source path or URL, and revision when
   available. If no ticket exists, do not substitute the prompt, a plan, or a
   diff for one; report the missing prerequisite and route the work to the
   repository's ticket-authoring workflow.
2. Read the ticket's goal, scope, acceptance criteria, constraints, and open
   questions. A diff can supplement the analysis or verify an implemented
   change, but it cannot define the intended change.
3. Read repository guidance and architecture documentation, then locate the
   concrete entry points with repository search: routes, commands, UI actions,
   exported APIs, jobs, event handlers, schemas, or configuration.
4. Trace the relevant execution and dependency paths in both directions. Follow
   callers, callees, shared types, persisted data, generated code, and tests far
   enough to explain why each reported impact exists.
5. Classify impact instead of treating every search hit as affected:
   - **direct**: required to implement the requested behavior;
   - **indirect**: depends on or is depended on by a direct impact;
   - **conditional**: affected only if a stated design choice is taken.
6. Check the boundaries that often hide structural consequences: public APIs,
   compatibility, data migrations, authorization, validation, caching,
   asynchronous work, observability, deployment configuration, and generated
   artifacts. Include only categories relevant to the actual repository.
7. Identify existing patterns or extension points that reduce the blast radius.
   Do not prescribe new abstractions when the codebase already has a suitable
   path.

## Evidence discipline

- Cite repository-relative paths and symbols for concrete findings; add line
  numbers when they are stable and useful.
- Label conclusions as **confirmed**, **inferred**, or **unknown**. A plausible
  architecture is not evidence that the repository uses it.
- Explain the dependency path for non-obvious impacts. Do not emit a flat list
  of filenames without reasons.
- Distinguish current code facts from recommended changes.
- Keep technical assumptions in the analysis. Treat unclear product behavior,
  changed acceptance criteria, and scope expansion as ticket issues rather than
  silently resolving them in the analysis.
- Reference ticket requirements instead of creating a second authoritative copy
  of them. Report contradictions between ticket and code explicitly.
- Do not modify production code, create a plan, approve the design, or broaden
  the task unless the user separately asks for that work.

## Output

Return an `impact` YAML mapping containing:

- a summary of the blast radius and the most consequential risk;
- technical assumptions and ticket issues;
- direct, indirect, and conditional impacts with evidence;
- API and data consequences where applicable;
- test and operational consequences where applicable;
- risks, open decisions, and unknowns;
- a compact dependency path or Mermaid diagram only when it makes the impact
  materially easier to understand.

Use the repository's existing schema when one exists. Otherwise use this shape,
omitting individual object properties that do not apply while keeping empty
top-level lists as `[]`:

```yaml
impact:
  summary: Expected blast radius and most consequential risk
  assumptions: []
  ticketIssues: []
  files:
    - path: src/example.ts
      scope: direct
      confidence: confirmed
      reason: Why this location is affected
      expectedChange: What is expected to change
  modules: []
  interfaces: []
  data: []
  dependencies: []
  verification: []
  operations: []
  risks: []
  decisions: []
  unknowns: []
```

Entries in `modules`, `interfaces`, `data`, and `dependencies` use the same
`scope`, `confidence`, `reason`, and `expectedChange` fields plus the identity
fields needed for that element. Risks state a title, severity, description, and
mitigation when known. Decisions state the question, status, considered options,
and resolution when decided.

Keep the mapping proportional to the change. For a read-only request, return it
without editing files. When the user asks to update or prepare the ticket,
replace only the top-level `impact` mapping in the existing YAML ticket. Preserve
`schemaVersion`, `ticket`, `plan`, and any unrelated fields, then parse the
resulting YAML to verify its syntax. Never create a separate impact file.
