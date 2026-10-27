# CLAUDE.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks (typos, obvious one-liners), use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing, briefly state:
- Key assumptions (or say “none”)
- Ambiguities or multiple interpretations (if any)
- Whether a simpler approach exists

If uncertain → stop and ask. Do not pick silently.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked
- No abstractions for single-use code
- No “flexibility” or “configurability” that wasn’t requested
- No error handling for impossible scenarios
- If 200 lines could be 50, rewrite it

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

The test: Every changed line should trace directly to the user’s request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- “Add validation” → “Write tests for invalid inputs, then make them pass”
- “Fix the bug” → “Write a test that reproduces it, then make it pass”
- “Refactor X” → “Ensure tests pass before and after”

For multi-step tasks, state a short plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
```

Before declaring done: confirm the success criteria are met (test, command, or explicit check). Do not rely on “it looks correct.”

---

**Working indicators:** fewer unnecessary diff changes, fewer rewrites from overcomplication, clarifying questions before implementation, clean minimal PRs.

See `EXAMPLES.md` for concrete illustrations of each principle.
