---
name: review-implementation
description: Review implementation against provided markdown requirements, specs, PRDs, or phase docs; optionally apply focused fixes. Use when a user supplies .md file paths and asks to verify correctness/completeness, check PRD phase completion, find missing or overbuilt work, assess critical issues, refactor long files/functions, or update code to match the docs.
---

# Review Implementation

## Overview

Review code against markdown requirements and produce evidence-backed findings.
When the user asks for fixes, apply targeted changes that bring the
implementation back to the docs without expanding scope.

## Modes

- Use **review-only mode** when the user asks to review, assess, audit, verify,
  or find issues.
- Use **fix mode** when the user asks to fix, update, refactor, complete,
  apply changes, or make the implementation match the docs.
- In fix mode, keep changes minimal and reversible. Do not add features that are
  not justified by the docs.

## Workflow

### 1) Intake and Discovery Gate

- Read all provided .md files and extract explicit requirements, constraints, and acceptance criteria.
- Read repo guidance such as AGENTS.md, README, architecture notes, and existing
  task or PRD files when relevant.
- Inspect affected code, tests, fixtures, routes, schemas, migrations, services,
  components, permissions, config, and observability surfaces as needed.
- Identify the current behavior, expected behavior, data flow, integration
  points, validation options, and likely blast radius.
- Ask only when a critical decision cannot be made safely after discovery.

### 2) Map Requirements to Evidence

- Build an internal traceability map: requirement -> status -> code evidence ->
  gap -> action.
- Classify each requirement as satisfied, partial, missing, conflicting,
  overbuilt, or deferred.
- Use file/line evidence for important claims. Do not rely on general
  impressions when code can be inspected.

### 3) Run Multi-Pass Review

Review in this order:

1. Requirements coverage: every requirement is satisfied or explicitly
   unresolved.
2. Correctness: happy paths, edge cases, errors, empty states, permissions,
   state transitions, and rollback behavior are handled.
3. Integration: changed modules fit together without contract breaks,
   duplicated ownership, or hidden assumptions.
4. Simplicity: the solution is no more complex than necessary.
5. Cleanup: repeated logic, dead code, temporary code, noisy logs, unused files,
   and unused dependencies are removed.
6. Security/privacy: auth, access control, secrets, sensitive data, injection
   risks, and audit needs are safe.
7. Performance: expensive queries, N+1 patterns, unnecessary renders, redundant
   network calls, and blocking work are addressed.
8. Validation: chosen checks are appropriate for the risk.
9. Documentation/operability: docs, release notes, migrations, rollback,
   monitoring, or support notes are updated when required.

Treat overbuilt code as a review finding when it adds features, abstractions,
state, dependencies, or workflow paths not required by the docs.

### 4) Apply Focused Fixes

- Fix issues directly in code with minimal, targeted changes.
- Split overly long files/functions only when the split reduces real review or
  maintenance risk.
- Remove or simplify overbuilt code that is not justified by the docs.
- Preserve existing patterns unless the docs or code evidence justify a change.
- If PRD or phase files are part of the request, update checkboxes, validation
  notes, discoveries, and change logs only when implementation evidence supports
  the update.

### 5) Validate with Evidence

- Choose the smallest sufficient validation for the risk: static checks, unit
  tests, integration tests, API-level E2E, browser/UI checks, simulator checks,
  screenshots, manual smoke checks, or observability checks.
- Run relevant checks when available and appropriate. If checks are unavailable,
  too costly, or not allowed, state the gap and use the best available evidence.
- Do not run broad or expensive validation by reflex when a narrower check proves
  the changed behavior.

## Report Format

Lead with the result that matters most:

- In review-only mode, list findings first in severity order with file/line
  references, then summarize coverage, validation, and residual risk.
- In fix mode, summarize fixes applied, validation performed, and any remaining
  findings or risks.
- If no issues are found, say so clearly and name any validation gaps.
- For critical blockers, stop and ask. For non-critical ambiguity, make the best
  reasonable decision, record the assumption, and continue.
