---
name: prd
description: Create or update a lean living Product Requirements Document through repeated drafting and subtraction. Use when defining a feature, planning implementation, revising a PRD or checklist as work progresses, or removing speculative scope and unnecessary design detail.
---

# PRD

Create a concise living document that keeps implementation aligned with its purpose. Do not implement unless the user asks.

## Philosophy

Follow the Unix and X11 philosophies:

- Define one clear purpose and the smallest complete result that achieves it.
- Prefer small, composable mechanisms and explicit interfaces.
- Do not plan for an imagined future. Avoid speculative scope, compatibility, policy, abstraction, and detail.
- Describe defensive behavior, fallback, retry, or recovery only when a real boundary, requirement, or failure cost justifies it. Allow internal invariant violations to fail visibly.
- Treat easy deletion as a design goal. Keep features and modules loosely coupled enough to remove independently.
- Choose the simplest design and implementation that fully satisfies the goal.
- Use direct language. State each fact and decision once; remove boilerplate, repetition, and decorative prose.

The PRD is a working aid, not a contract or ceremony. Its value is the clarity of the decisions and checklist, not its length.

## Draft in Passes

Do not try to finish the PRD in one pass:

1. **Intent:** write the purpose, goals, non-goals, and observable success conditions.
2. **Execution:** add only material constraints and a concrete, verifiable, dependency-ordered implementation and validation checklist.
3. **Subtraction:** remove imagined future needs, unjustified defenses, premature architecture, optional scope, and details that do not change implementation.
4. **Clarity:** remove repetition, boilerplate, vague wording, and decorative prose. Keep one clear source for each idea.

Inspect relevant existing code and documents before committing to a design. Repeat the passes until every remaining line helps decide, implement, or verify the work.

## Living Checklist

- Make every item small enough to complete and verify clearly.
- Include validation in the same checklist as implementation.
- Use phases only when they make dependencies or progress clearer.
- Check off completed work as evidence appears.
- During implementation, repeatedly add, remove, split, merge, or reorder items as discoveries change the simplest sufficient path.
- Keep the PRD as the single current plan; update it instead of preserving an obsolete plan beside the real work.
- Preserve the purpose and meaningful decisions when the checklist changes. Record only consequential changes.

Finish when the success conditions are proven and no unnecessary scope remains. Prefer one concise Markdown file unless the user or project requires another structure.
