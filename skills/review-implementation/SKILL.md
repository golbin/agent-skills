---
name: review-implementation
description: Review implementation against its purpose and user experience, fix root causes, and refine it through repeated simplification passes. Use when verifying correctness and side effects, reviewing user-facing or developer-facing interfaces, redesigning flawed foundations, managing legacy compatibility, removing speculative abstractions or defensive code, or applying fixes.
---

# Review Implementation

Review from evidence. Protect the purpose first, then simplify repeatedly.

## Philosophy

Follow the Unix and X11 philosophies:

- Make each part do one thing well.
- Prefer small, composable mechanisms; keep policy and side effects at explicit boundaries.
- Treat every interface as a user experience, whether its user is a customer, developer, operator, or another system. Optimize for their outcome, predictability, and cost of use, not implementation convenience or feature count.
- Choose the simplest coherent system that fully achieves the purpose, not the smallest diff. Effort or change size is not a reason to preserve a wrong foundation.
- Fix root causes instead of adding compensating branches, wrappers, flags, or special cases around them.
- Do not design for an imagined future. Add abstraction only when a present need or real duplication justifies it.
- Defend real boundaries and failures, not every conceivable case. At trusted internal boundaries, prefer an immediate, visible failure to fallback, retry, catch-and-continue, or invalid state. At a user boundary, make the failure specific and actionable.
- Preserve legacy behavior only when actual users, data, or public contracts justify it. Isolate compatibility at a boundary, provide a migration path, and make its removal explicit; do not distort the core design or maintain parallel paths indefinitely.
- Treat easy deletion as the strongest test of good modularity. A feature or module should be removable with few unrelated changes.
- Write code, comments, and documents plainly. State each idea once; remove ceremony, repetition, and decorative language.

Simplicity is not fewer lines at the expense of correctness. Keep everything required by the goal and nothing else.

## Review Cycle

Work in this order. Do not collapse all concerns into one pass.

### 1. Purpose and correctness

- Verify that the implementation achieves the intended goal and requirements.
- Trace the relevant interface, callers, data flow, and user workflow before changing it. Judge the result from the user's path, not only the local code.
- Find incorrect, missing, or conflicting behavior.
- Trace material problems to their root cause. Decide whether a local fix is sound or the model, ownership, boundary, or flow must change.
- Separate intended contracts from accidental legacy behavior. Treat prescribed designs as revisable when they conflict with the purpose or evidence.
- Redesign freely within the authorized purpose. Surface material changes to product intent, public contracts, data, or rollout before acting.
- Check relevant edge cases, integration boundaries, and potential security, data, performance, or operational problems.
- Look for unintended behavior and side effects outside the changed scope.
- Validate the user-observable outcome and important contracts with the smallest sufficient checks.

### 2. Refine in focused passes

Run several small passes:

1. **Repair the foundation:** replace a flawed model, boundary, ownership split, or flow instead of patching around it, even when the coherent change is larger.
2. **Subtract scope:** remove behavior, options, dependencies, temporary work, and future-facing paths not required by the purpose.
3. **Collapse structure:** remove needless layers, indirection, state, abstractions, wrappers, and defensive branches. Prefer direct failure when recovery has no requirement or user value.
4. **Isolate legacy:** keep justified compatibility in a removable adapter or migration, with one target model and a clear retirement condition.
5. **Clarify use:** keep interfaces small, explicit, consistent, and hard to misuse. Use intention-revealing names and clear errors; make docs and tests useful as examples. Remove duplication, restatement, and ornamental prose.

After each pass, preserve intended behavior with proportionate checks. Then repeat the purpose review and refinement passes until a full pass finds no meaningful problem or simplification. Do not stop after the first acceptable result.

## Act and Report

- When asked only to review, report findings in severity order with concrete evidence and validation gaps.
- When asked to improve or fix, implement the simplest coherent end state, not the smallest patch. Make the broader change when the root cause requires it; leave a workaround only when explicitly temporary, with a removal condition. Validate the final result and report remaining risk.
- State clearly when no material issue is found.
