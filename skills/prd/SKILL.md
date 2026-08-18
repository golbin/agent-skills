---
name: prd
description: Create or update a lean, user-centered living Product Requirements Document through repeated drafting and subtraction. Use when defining a feature or interface, planning root-cause or architectural work, revising implementation as discoveries emerge, handling legacy migration, or removing speculative scope and unnecessary design detail.
---

# PRD

Create a concise living document that keeps implementation aligned with its purpose. Do not implement unless the user asks.

## Philosophy

Follow the Unix and X11 philosophies:

- Define one clear purpose and the simplest coherent end state that fully achieves it, not the smallest diff or least-effort transition.
- Start from the user's task and desired outcome. Treat UI, APIs, functions, CLIs, and operational surfaces alike as user experiences; optimize for predictability and low cognitive cost.
- Prefer small, composable mechanisms and explicit interfaces; confine policy and side effects to boundaries.
- Replace a wrong foundation when the purpose requires it; effort alone is not a reason to preserve it.
- Do not plan for an imagined future. Avoid speculative scope, compatibility, policy, abstraction, and detail.
- Describe defensive behavior, fallback, retry, or recovery only when a real boundary, requirement, or failure cost justifies it. Allow internal invariant violations to fail visibly, and make boundary failures actionable to their users.
- Preserve legacy behavior only for known users, data, or contracts. Keep compatibility outside the target design in a removable adapter or migration, and define when it ends.
- Treat easy deletion as a design goal. Keep features and modules loosely coupled enough to remove independently.
- Use direct language. State each fact and decision once; remove boilerplate, repetition, and decorative prose.

The PRD is a working aid, not a contract or ceremony. Its value is the clarity of the decisions and checklist, not its length.

## Draft in Passes

Do not try to finish the PRD in one pass:

1. **Intent:** identify the user, their task and friction, the desired outcome, goals, non-goals, and user-observable success conditions.
2. **Execution:** identify the root cause and target design, then add only material constraints and a concrete, verifiable, dependency-ordered implementation and validation checklist. Include compatibility and migration only when evidence requires them.
3. **Subtraction:** remove imagined future needs, unjustified defenses, premature architecture, optional scope, local workarounds, permanent transition layers, and details that do not change implementation.
4. **Clarity:** remove repetition, boilerplate, vague wording, and decorative prose. Keep one clear source for each idea.

Inspect relevant existing interfaces, callers, workflows, code, and documents before committing to a design. Repeat the passes until every remaining line helps decide, implement, or verify the work.

## Living Checklist

- Make every item small enough to complete and verify clearly.
- Include validation of the actual user workflow and interface contracts in the same checklist as implementation.
- Use phases only when they make dependencies or progress clearer.
- Check off completed work as evidence appears.
- During implementation, repeatedly add, remove, split, merge, or reorder items as discoveries change the simplest sufficient path.
- When discoveries invalidate the design, rewrite the target and checklist instead of appending compensating tasks around a flawed plan.
- Keep the PRD as the single current plan; update it instead of preserving an obsolete plan beside the real work.
- Preserve the purpose and meaningful decisions when the checklist changes. Record only consequential changes.

Finish when the success conditions are proven and no unnecessary scope remains. Prefer one concise Markdown file unless the user or project requires another structure.
