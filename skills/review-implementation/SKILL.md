---
name: review-implementation
description: Review implementation against its purpose, then refine it through repeated simplification passes. Use when verifying correctness and side effects, removing speculative abstractions or defensive code, simplifying design and writing, or applying focused fixes.
---

# Review Implementation

Review from evidence. Protect the purpose first, then simplify repeatedly.

## Philosophy

Follow the Unix and X11 philosophies:

- Make each part do one thing well.
- Prefer small, composable mechanisms to policy-heavy frameworks.
- Choose the simplest design and implementation that fully achieves the purpose.
- Do not design for an imagined future. Add abstraction only when a present need or real duplication justifies it.
- Defend real boundaries and failures, not every conceivable case. At trusted internal boundaries, prefer an immediate, visible failure to fallback, retry, catch-and-continue, or invalid state.
- Treat easy deletion as the strongest test of good modularity. A feature or module should be removable with few unrelated changes.
- Write code, comments, and documents plainly. State each idea once; remove ceremony, repetition, and decorative language.

Simplicity is not fewer lines at the expense of correctness. Keep everything required by the goal and nothing else.

## Review Cycle

Work in this order. Do not collapse all concerns into one pass.

### 1. Purpose and correctness

- Verify that the implementation achieves the intended goal and requirements.
- Find incorrect, missing, or conflicting behavior.
- Check relevant edge cases, integration boundaries, and potential security, data, performance, or operational problems.
- Look for unintended behavior and side effects outside the changed scope.
- Validate important claims with the smallest sufficient checks.

### 2. Refine in focused passes

Run several small passes:

1. **Subtract scope:** remove behavior, options, dependencies, temporary work, and future-facing paths not required by the purpose.
2. **Collapse structure:** remove needless layers, indirection, state, abstractions, wrappers, and defensive branches. Prefer direct failure when recovery has no requirement or user value.
3. **Clarify expression:** shorten names, control flow, comments, tests, and docs; remove duplication, restatement, and ornamental prose.
4. **Recheck boundaries:** consolidate repeated knowledge only when one clear owner reduces coupling. Reject commonization that merely moves or hides complexity.

After each pass, preserve behavior with proportionate checks. Then repeat the purpose review and refinement passes until a full pass finds no meaningful problem or simplification. Do not stop after the first acceptable result.

## Act and Report

- When asked only to review, report findings in severity order with concrete evidence and validation gaps.
- When asked to improve or fix, apply small coherent changes across the review cycle, validate the final result, and report what changed and any remaining risk.
- State clearly when no material issue is found.
