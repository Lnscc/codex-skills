---
name: project-overview
description: >
  Plan or document a project in one repository-local Markdown overview covering
  purpose, architecture, modules, key libraries, flows, configuration, and
  development workflows. Use before implementation to design a project, or
  afterward to refresh its living documentation against the codebase. Do not
  use for task-level implementation plans or production code changes.
---

# Project Overview

Maintain concise, evidence-backed Markdown that gives contributors a useful
mental model of the project.

## Workflow

1. Use the user- or repository-defined path. Otherwise update an existing
   matching document such as `docs/project-overview.md`, `ARCHITECTURE.md`, or
   `docs/architecture.md`; if none exists, create `docs/project-overview.md`.
   Never create a competing overview.
2. Build from the best available evidence. Before implementation, use stated
   goals, constraints, and repository conventions. As code exists, inspect
   relevant manifests, entry points, modules, configuration, persistence,
   integrations, tests, and deployment files.
3. Record rationale, assumptions, open decisions, and a high-level
   implementation order where useful. Keep proposals distinguishable from
   verified behavior without adding a project-status field.
4. Preserve accurate manual context, correct stale claims, and remove confirmed
   obsolete details. Check the diff for unsupported claims, broken relative
   links, lost content, and needless reformatting.

## Content

Adapt the structure to the project and document only useful, durable information:

- goals, scope, non-goals, and main capabilities;
- architecture, modules, responsibilities, and important flows;
- languages, frameworks, and notable libraries with roles and rationale;
- persistence, interfaces, integrations, and configuration;
- build, run, test, packaging, and deployment workflows;
- implementation phases, constraints, risks, open decisions, and key locations.

Prefer source evidence over folder-name guesses or stale prose. Use
repository-relative links and diagrams only when they improve understanding.
Avoid exhaustive inventories, speculative complexity, transient Git state,
timestamps, and versions that add no value. Mark proposals, inferences, and
unknowns; never invent implemented behavior.

Do not install dependencies, start services, or modify production code,
configuration, dependencies, or external systems for this documentation task.
