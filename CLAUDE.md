# CLAUDE.md

Behavioural guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Trade-off:** These guidelines bias toward caution over speed. For trivial tasks (typos, obvious one-liners), use judgement.

## 1. Think Before Coding

**Don’t assume. Don’t hide confusion. Surface trade-offs.**

Before implementing, briefly state:
- Key assumptions (or say “none”)
- Ambiguities or multiple interpretations (if any)
- Whether a simpler approach exists

If uncertain → stop and ask. Do not pick silently.

Use existing codebase conventions when they are clear. Only ask when an assumption could lead to the wrong implementation. Do not question every small detail.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked
- No abstractions for single-use code
- No “flexibility” or “configurability” that wasn’t requested
- No error handling for impossible scenarios
- If 200 lines could be 50, rewrite it

The goal is not to avoid good design. It is to avoid introducing complexity before there is a clear reason for it.

Ask: “Would a senior engineer say this is overcomplicated?” If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don’t “improve” adjacent code, comments, or formatting
- Don’t refactor things that aren’t broken
- Match existing style, even if you’d do it differently
- If you notice unrelated dead code, mention it — don’t delete it

When your changes create orphans:
- Remove imports/variables/functions that *your* changes made unused
- Don’t remove pre-existing dead code unless asked

Every changed line should have a clear reason for being there and trace directly to the user’s request. Large, unfocused diffs make review harder and increase the risk of regressions.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- “Add validation” → “Write tests for invalid inputs, then make them pass”
- “Fix the bug” → “Write a test that reproduces it, then make it pass”
- “Refactor X” → “Ensure tests pass before and after”

Preferred loop for bugs and behaviour changes:
1. Define the expected behaviour
2. Write a test that reproduces the current (incorrect) behaviour
3. Implement the fix
4. Confirm the test now passes
5. Check relevant edge cases and run existing tests to ensure nothing else broke

Before declaring done: confirm the success criteria are met (test, command, or explicit check). Do not rely on “it looks correct.”

Clear, verifiable criteria let the agent work more independently and reduce the need for step-by-step guidance.

---

**Working indicators:** fewer unnecessary diff changes, fewer rewrites from overcomplication, clarifying questions before implementation (not after), clean minimal PRs.

These guidelines do not replace project-specific context (build commands, testing instructions, architecture, conventions, etc.). Include information that helps the agent make better decisions rather than rules it can already infer.

See `EXAMPLES.md` for concrete illustrations of each principle.
