---
name: prd
description: Create or revise a concise product requirements document and living implementation checklist when planning a feature or updating its scope.
---

# PRD

Keep the user's outcome, the target design, and the remaining work in one concise
document grounded in the project. A planning-only request ends with the document;
when implementation is already requested, use the plan to continue that work.

## Establish the target

Inspect the interfaces, callers, code, or product evidence needed to understand
the requested change. Record the current problem, who encounters it, and the
observable result that would resolve it. Ask about a missing decision only when
it materially changes scope or correctness; record reasonable assumptions for
details that can be decided within the request.

Choose the simplest coherent end state that fully achieves the purpose. Fix a
wrong foundation when evidence requires it. Preserve the Unix/X11 preference for
small, composable mechanisms, explicit interfaces, and policy at boundaries.
Treat APIs, CLIs, functions, and operational tools as user experiences too.

Include compatibility, retries, recovery, and migration only for known users,
data, contracts, or failure costs. Keep necessary transition mechanisms removable
and give them a retirement condition. Avoid speculative features and abstractions.

## Write the working document

Follow the user's location or the project's existing convention; otherwise use
`tasks/prd-<feature>.md`. Reuse an existing PRD instead of creating a competing plan.

Capture what the executor needs to decide, implement, and verify:

- The problem, intended outcome, scope, and observable success conditions.
- Evidence that shapes the target design, material constraints, and open decisions.
- A dependency-aware checklist of concrete implementation and validation outcomes.
- Current status and consequential changes to the design or scope.

Scale the structure to the task. Use one file for a compact plan. Split out context
or phase files only when independent work or detailed evidence makes them useful;
link the files from the main PRD. Do not invent phases or sections to fill a template.

Validation items should name the behavior or contract to prove and the appropriate
available check. Do not require every test category or repeat successful checks
without a new change, failure, or unresolved risk.

## Keep it useful during execution

Preserve meaningful user edits and completed work. Check items off only when
supported by implementation or validation evidence, and distinguish pending
verification from completion. Revise affected items as discoveries change the
target; retain important requirements or explicitly record their deferral.

Review the draft for unsupported assumptions, unnecessary scope, and repetition.
Revise where that review finds a concrete problem. The document is ready when
another contributor can execute it and assess success without guessing material
decisions. Report the saved path and any decisions that still need the user.
