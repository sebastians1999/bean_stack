---
name: how
description: "Use for \"how does X work\", code walkthroughs before changing something, and placement / ownership / layering questions (\"where should this live\", \"which package owns this\", \"is this the right layer\"). Explains subsystem architecture, runtime flow, onboarding mental models. Use why for motivation."
disable-model-invocation: true
---

# How

Explore the codebase to answer "how does X work?" questions. Produce architectural explanations at the level of a senior engineer onboarding onto a subsystem, enough to build a working mental model, not so much that it reads like annotated source code.

Every spawn is a Task subagent with `subagent_type: generalPurpose` and `readonly: true`. Set `model` from the `how and why` role, per the Models table in the **sebastian-mode** skill. The reading happens in the subagent, so it stays out of the parent's context. Never more than two subagents per question.

## 1. Explain

If the scope is ambiguous, state your interpretation and explore. The user can redirect.

Spawn one explainer that explores and explains in one pass, built from `references/explainer-prompt.md` with an empty Notes section. This holds for a narrow question and for a whole subsystem.

## 2. Close a named gap (optional)

Spawn a second subagent only when the explanation names a gap one more read could close: a flow it could not trace, a boundary it did not reach, or an open question about a specific file or caller. Build it from `references/explorer-prompt.md` with that gap as its angle and the first explanation attached. It reads the gap only and returns the revised explanation. A gap you cannot name as a file, caller, or flow does not earn a second subagent. Never spawn a third.

## 3. Present

Present the latest explanation. Light edits for clarity or context from the conversation are fine. Do not substantially rewrite it.

## Output format

The explanation uses the sections defined in `references/explainer-prompt.md`, dropping any that do not apply: Overview, Key concepts, How it works, Where things live, Gotchas.
