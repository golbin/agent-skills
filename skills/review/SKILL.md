---
name: review
description: Review software designs and implementations for user experience, simplicity, and maintainability; apply changes when requested. Use for design critiques, implementation audits, or specification conformance reviews.
---

# Review

Judge designs and implementations by the experience they deliver to their users.
Among solutions that meet the user's needs and required contracts, simplicity is
the most important design criterion.

## Choose the requested mode

For a review, audit, or assessment, inspect and report without editing design
documents, code, or requirement status. When fixes or improvements are requested,
apply them within the agreed purpose. Existing authorization carries through the
work; the skill does not add a separate approval step.

## Start with the user experience

Identify who uses the result and what they need to accomplish. End users,
API consumers, developers maintaining server logic, and operators all count.
Evaluate whether their workflow is understandable, predictable, and recoverable,
including setup, normal use, failures, and later changes where relevant.
Correctness, security, data integrity, and required compatibility are part of
that experience; do not sacrifice them to reduce code or steps.

Use supplied requirements, PRDs, acceptance criteria, and project guidance. For
a design, trace proposed interactions, ownership, contracts, and data flow through
concrete scenarios; identify assumptions that need evidence. For an
implementation, trace affected callers, interfaces, and tests far enough to judge
the complete workflow. Distinguish intended requirements from accidental legacy
behavior. A design review does not require code to exist.

Connect material findings to evidence and a specific user consequence or
maintenance cost. Check cross-boundary risks such as stale async results,
duplicated work, data loss, or incompatible contracts when the reviewed behavior
exposes them. Avoid a universal checklist of unrelated concerns.

## Prefer simplicity and easy removal

Follow the Unix philosophy: give each part one focused job and compose small
mechanisms through explicit interfaces. Separate policy from mechanism and keep
side effects at boundaries when this clarifies ownership. Choose the fewest
concepts, dependencies, states, and indirections that solve the actual problem;
composition does not require extra services, frameworks, or abstractions.

Use deletability as a test of modularity: can a feature or component be removed
with few unrelated changes? Clear ownership and limited coupling make removal,
replacement, extension, and maintenance easier. Prefer modules whose lifecycle
is local over speculative extension points or shared state that spreads a change
through the system. Do not add machinery merely to demonstrate removability.

## Improve when authorized

Fix the root cause with the simplest coherent design. A larger structural change
is justified when a smaller patch would preserve the fault. Remove unnecessary
layers, duplication, state, or options when this resolves a demonstrated problem
within scope. Do not discard behavior merely because its consumer is absent from
the local diff. Preserve compatibility and recovery required by known users,
data, or contracts; isolate temporary compatibility and define its retirement.

If a fix requires a product, public-contract, data, or rollout decision outside
the request, present that decision and continue independent work within scope.

Use the smallest sufficient checks for the changed behavior and its contracts,
subject to project execution rules. For designs, use scenario walkthroughs and
contract checks; distinguish proposed validation from checks actually run.
Recheck after a relevant change, failure, or unresolved concern. Finish when the
authorized findings are addressed and the evidence is sufficient; simplification
is not an open-ended goal. Update requested requirement status only when the
work and evidence support it, and record deferred work or validation gaps.

## Report

For review-only work, lead with actionable findings in severity order, each with
a design section or file/line reference, the affected scenario, and its
consequence. For fix work, lead with changes and validation performed. State when
no material issue was found and distinguish inspection from execution evidence.
