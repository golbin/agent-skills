---
name: review
description: Review software designs and implementations for user experience, simplicity, and maintainability; apply fixes when requested.
---

# Review

Put user experience first. Choose the simplest solution that meets the need while
preserving correctness, security, user data, and required contracts.

## Scope

Review-only requests authorize inspection and findings, without edits to code,
design documents, or requirement status. Apply requested fixes within the agreed
scope; existing authorization does not need a separate approval step.

## Evaluate

Identify users and their tasks, including API consumers, maintaining developers,
and operators. Assess whether workflows are understandable, predictable, and
recoverable in normal use, failure, and later maintenance.

Use relevant requirements and project guidance. Walk designs through concrete
scenarios, ownership, contracts, and data flow. For implementations, trace callers,
interfaces, and tests across the affected workflow. Distinguish assumptions and
accidental legacy behavior from intended requirements. Investigate risks such as
stale results, duplicates, or data loss when the reviewed behavior exposes them.

Follow Unix philosophy: focused parts composed through explicit interfaces, with
policy separated from mechanism and side effects at boundaries. Minimize concepts,
dependencies, state, and indirection; avoid speculative abstractions.

Test modularity by asking whether a component can be removed with few unrelated
changes. Local ownership and limited coupling make deletion, replacement,
extension, and maintenance easier. Do not add machinery just for removability.

## Fix and verify

When authorized, fix root causes. Restructure when a smaller patch would preserve
the fault; remove unnecessary layers or duplication within scope. A consumer's
absence from the local diff is not evidence that behavior is unused. Preserve
required compatibility and recovery; give temporary mechanisms a retirement
condition.

Raise product, contract, data, or rollout decisions outside the request while
continuing independent work within scope.

Use the smallest sufficient checks allowed by project rules, including scenario
walkthroughs for designs. Recheck only after a relevant change, failure, or
unresolved concern. Finish when authorized findings are addressed and evidence is
sufficient. Update requested requirement status only with supporting evidence.

## Report

For reviews, lead with actionable findings in severity order: location (design
section or file/line), evidence, affected scenario, and user or maintenance impact.
State when no material issue was found. For fixes, lead with changes and validation.
Distinguish inspection, checks actually run, and proposed checks; record deferred
work and validation gaps.
