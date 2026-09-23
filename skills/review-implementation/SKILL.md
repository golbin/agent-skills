---
name: review-implementation
description: Review an implementation against its requirements and user workflow; apply fixes when requested. Use for implementation audits or specification conformance reviews.
---

# Review Implementation

Establish whether the implementation achieves its intended purpose and identify
concrete problems in behavior, contracts, or structure.

## Choose the requested mode

For a review, audit, or assessment, inspect and report without editing code or
marking requirements complete. When fixes or improvements are requested, apply
them within the agreed purpose. Existing authorization carries through the work;
the skill does not add a separate approval step.

## Ground the review

Use supplied requirements, PRDs, acceptance criteria, and relevant project
guidance. Trace affected callers, interfaces, data flow, and tests far enough to
judge the user's complete workflow. Distinguish documented requirements from
assumptions and accidental legacy behavior.

For material findings, connect the expected outcome to code evidence and a
specific failure or maintenance cost. Check cross-boundary effects such as stale
async results, duplicated work, data loss, or incompatible contracts when the
changed behavior exposes those risks. Avoid a universal checklist of unrelated
security, performance, or cleanup work.

Treat each interface as a user experience, including APIs, CLIs, functions, and
operator tools. Evaluate whether it is predictable and supports its user's task.

## Improve when authorized

Fix the root cause with the simplest coherent design. A larger structural change
is justified when the evidence shows a smaller patch would preserve the fault;
review alone does not authorize that change. If the fix requires a product,
public-contract, data, or rollout decision outside the request, present that
decision and continue independent work within the agreed scope.

Prefer small, composable mechanisms, explicit interfaces, and policy and side
effects at boundaries. Remove unnecessary layers, duplication, state, or options
when doing so resolves a demonstrated problem in the reviewed scope. Do not
discard behavior merely because its consumer is not visible in the local diff.

Keep compatibility and recovery that known users, data, or contracts require.
Isolate temporary compatibility and define when it can be retired. Let invalid
internal state fail visibly; make failures at user-facing boundaries actionable.

Use the smallest sufficient checks for the changed behavior and its contracts,
subject to project execution rules. Recheck after a relevant change, failure, or
unresolved concern. Finish when the authorized findings are addressed and the
evidence is sufficient; additional simplification is not an open-ended goal.

Update requested PRD status or checkboxes only when the work and evidence support
them. Record deferred requirements and validation gaps explicitly.

## Report

For review-only work, lead with actionable findings in severity order, each with
file/line evidence, the affected scenario, and its consequence. For fix work,
lead with the changes and the validation performed. State when no material issue
was found, and distinguish code inspection from checks actually run.
