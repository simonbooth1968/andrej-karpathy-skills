# Transcript: The 4 Lines Every CLAUDE.md Needs that Make Claude 100x Better

**Channel:** Cloud X Berry  
**Video:** [The 4 Lines Every CLAUDE.md Needs that Make Claude 100x Better](https://youtu.be/MqMD3Rbvl0Q)  
**Duration:** ~5:46  

> Note: This is a cleaned and corrected transcript in British English, reconstructed from the video’s chapters, description, and content. It is not a raw auto-generated caption dump.

---

## Introduction

AI coding agents can write code, fix bugs, and build features. But if you’ve used them on real projects, you’ve probably run into the same frustrating habits.

They make assumptions without asking.  
They turn a simple requirement into a complicated implementation.  
They change code nobody asked them to touch.  
And they say everything works without testing it.

These aren’t random mistakes. They are habits. And four short lines in your Claude Code instructions can change them.

The principles come from Andrej Karpathy’s observations, turned into an open-source GitHub project. We’ll go through each one with a concrete example.

## Principle 1: Don’t assume

An agent asked to export user data picks JSON, includes every user, and writes a file — all before checking a single requirement.

It never stops to ask:
- Which format?
- All users or a filtered set?
- Which fields?
- File download, API response, or something else?

**The rule:** Don’t assume. If something is unclear, stop and ask. Surface the trade-offs instead of picking silently.

## Principle 2: Minimum code, nothing speculative

A percentage-discount function that should be three lines becomes a set of classes, interfaces, and config objects.

The agent added flexibility and abstractions that were never requested.

**The rule:** Write the minimum code that solves the problem. Nothing speculative. If a senior engineer would say it’s overcomplicated, simplify it.

## Principle 3: Touch only what you must

A one-line email validation fix turns into a sprawling diff of renamed variables, reformatted files, and “improved” surrounding code.

The agent touched things that had nothing to do with the bug.

**The rule:** Make surgical changes. Only modify what is required for the task. Clean up only the mess you just created. Match the existing style.

## Principle 4: Define success criteria

An authentication bug: changing a password should log out existing sessions. The agent claims the fix is done after editing the code — but never proves that old sessions are actually invalidated.

**The rule:** A task is not finished until it is verified. Transform the request into a checkable goal (write a failing test, make it pass, confirm no regressions). Do not declare success based on the code looking correct.

## Where to find the guidelines

These four principles live in a single `CLAUDE.md` file (and as a Claude Code skill). You can add them to any project. They do not replace your own project context — stack, commands, conventions, and constraints still belong in the file — but they provide strong behavioural guardrails.

## Recap: the four things to focus on

Whenever you work with an AI coding agent, focus on these four things:

1. **Understand the requirements** — don’t assume.
2. **Keep solutions simple** — minimum code, nothing speculative.
3. **Limit changes** — touch only what you must.
4. **Verify the result** — define success criteria and loop until they are met.

These four short lines catch the majority of the frustrating behaviour that makes AI coding agents feel unreliable on real projects.

---

*End of transcript.*
