---
name: prd
description: Create or update a concise PRD and implementation checklist for a feature or scope change.
---

# PRD

Keep the user's outcome, target design, and remaining work in one document.
Planning-only requests end with the PRD; continue implementation when already
requested.

## Define the target

Read the project evidence needed to identify the problem, affected users, and
observable success conditions. Ask about missing decisions that materially affect
scope or correctness; record reasonable assumptions for other details.

Choose the simplest design that meets the need, correcting the foundation when
necessary. Follow Unix philosophy: focused, composable parts, explicit interfaces,
and policy and side effects at boundaries. APIs and internal tools also serve
users, including developers and operators.

Include compatibility, recovery, retries, or migration for concrete user, data,
contract, or failure risks. Keep temporary mechanisms removable with a retirement
condition. Avoid speculative features and abstractions.

## Write the document

Update an existing PRD when available. Otherwise follow the requested location or
project convention, defaulting to `tasks/prd-<feature>.md`.

Include:

- Problem, intended outcome, scope, and success conditions.
- Target design, supporting evidence, constraints, and open decisions.
- A checklist ordered by dependencies, with implementation and validation outcomes.
- Current status and consequential design or scope changes.

Use only the sections the task needs. Split out linked files when detailed
evidence or independent work warrants it. Validation items should identify the
behavior or contract to prove and a suitable check allowed by project rules.

## Maintain and finish

Preserve user edits and completed work. Update the plan as evidence changes;
record deferred requirements and distinguish implemented work from verified work.
Mark items complete only with supporting evidence. Repeat checks only after a
relevant change, failure, or unresolved concern.

Remove unsupported assumptions, unnecessary scope, and repetition. The PRD is
ready when another contributor can execute it and judge success without guessing
material decisions. Report its path and decisions still requiring the user.
