# Transcript: The 4 Lines Every CLAUDE.md Needs that Make Claude 100x Better

**Channel:** Cloud X Berry  
**Video:** [The 4 Lines Every CLAUDE.md Needs that Make Claude 100x Better](https://youtu.be/MqMD3Rbvl0Q)

---

AI coding agents can write code, fix bugs, and build features. But if you’ve used them on real projects, you’ve probably noticed a few frustrating habits. They make assumptions without asking questions, turn simple requirements into complicated implementations, modify unrelated code, and sometimes claim everything works without properly testing it. A GitHub project called Andrej Karpathy Skills turned those observations into four behavioural principles for Claude Code. Let’s look at each principle and understand how it can change the way an AI coding agent approaches your work.

## Principle 1: Don’t assume. Don’t hide confusion. Surface trade-offs.

Imagine asking an AI agent to build a feature that exports user data. The agent immediately implements JSON export, includes every user, and saves the results to a file. The implementation might work perfectly, but it has made several decisions you never specified. Maybe you wanted CSV. Perhaps users should be able to export only their own data. Some fields might contain sensitive information that shouldn’t be included. The problem is that the agent chose an implementation before understanding the requirements.

This principle encourages the agent to identify important uncertainties and ask questions before making decisions that could affect the result. It should clarify the output format, the required fields, and the expected scope of the export when those details aren’t already clear from the project. That doesn’t mean asking questions about every small detail. If the existing codebase already establishes a convention, the agent should use it. The important distinction is knowing when it has enough information to proceed and when an assumption could lead to the wrong implementation.

## Principle 2: Minimum code that solves the problem. Nothing speculative.

Another common problem is unnecessary complexity. Let’s say you need a function that calculates a percentage discount. The calculation itself is straightforward, but an AI agent might introduce several classes, abstract interfaces, and configuration objects to handle it. Those patterns can be useful in larger systems, but for a simple calculation, they may introduce complexity without providing any real benefit. Every additional abstraction creates more code to understand, test, and maintain.

This principle encourages the agent to solve the actual requirement using the simplest reasonable implementation. If the project later needs multiple discount strategies or a configurable pricing engine, you can introduce those abstractions when the requirements justify them. Until then, there’s no need to build an architecture around possibilities that might never happen. The goal isn’t to avoid good design. It’s to avoid introducing complexity before there’s a clear reason for it.

## Principle 3: Touch only what you must. Clean up only your own mess.

Suppose you ask an agent to fix a bug in email validation. Instead of making the required change, it also modifies username validation, renames variables, reformats nearby functions, and changes unrelated files. Now you have a much larger diff to review. Even though the original task involved one specific bug, this creates unnecessary work and makes it harder to identify which changes might introduce regressions.

The principle here is to keep modifications focused on the requested task. Every changed line should have a clear reason for being there. If the agent introduces an unused import or a dead variable while fixing the bug, it should clean up its own changes. However, it shouldn’t start rewriting unrelated code simply because it notices something it could improve. This is especially important in established codebases where seemingly harmless changes can affect other features or make code reviews unnecessarily difficult. Smaller focused changes are easier to understand, test, and maintain.

## Principle 4: Define success criteria. Loop until verified.

Writing the code is only part of completing a task. The agent also needs to establish whether the implementation actually works. Let’s say you’re fixing an authentication bug where changing a password should invalidate existing sessions. Simply modifying the authentication logic doesn’t prove that the problem is fixed. A better approach is to define the expected behaviour first, write a test that reproduces the bug, implement the fix, and run the test again. The agent should also check relevant edge cases and run existing tests to make sure the change hasn’t broken other functionality. If a test fails, it should investigate the failure, make the necessary correction, and test again.

This principle gives the agent a concrete definition of completion rather than allowing it to decide that a task is finished simply because it has generated the code. It also reduces the need for you to guide every individual step. When success criteria are clear and verifiable, the agent can work through the implementation and validation process more independently.

## Putting the four principles into practice

You can find these guidelines in the forrestchang/andrej-karpathy-skills GitHub repository, which provides the behavioural principles along with examples of how they apply to coding tasks. They provide a useful foundation for your Claude Code instructions, but they don’t replace project-specific context. Your agent may still need build commands, testing instructions, architectural decisions, security requirements, and conventions that aren’t obvious from the existing code. The key is to include information that helps the agent make better decisions rather than filling its configuration with rules it can already infer.

When you use an AI coding agent, focus on four things. Make sure it understands the requirement. Keep the solution simple. Limit changes to what the task requires. And verify the result before calling it complete. These principles help address some of the most frustrating habits in AI-assisted programming while keeping the developer responsible for the decisions that matter.

---

*Transcript cleaned and corrected for British English spelling and grammar.*
