---
name: how
description: "Use for \"how does X work\", code walkthroughs before changing something, and placement / ownership / layering questions (\"where should this live\", \"which package owns this\", \"is this the right layer\"). Explains subsystem architecture, runtime flow, onboarding mental models. Use why for motivation."
disable-model-invocation: true
---

# How

Explore the codebase to answer "how does X work?" questions. Produce an architectural explanation at the level of a senior engineer onboarding onto a subsystem. Enough to build a working mental model. Not so much that it reads like annotated source code.

Do the read in this agent. Spawn one helper only when the subsystem is too large to hold here.

## 1. Assess complexity

If the scope is ambiguous, state your interpretation and explore. The user can redirect.

- **Fits here** (a single module, a small utility, a narrow question, or a subsystem you can read in this chat). No subagent. Read the code and write the explanation yourself, using the sections in `references/explainer-prompt.md`. Go to step 3.
- **Too large to hold here.** Go to step 2.

When in doubt, do it here.

## 2. One helper

Spawn one Task subagent with `subagent_type: generalPurpose` and `readonly: true`. Set `model` from the `how and why` role, per the Models table in the **sebastian-mode** skill. Build its prompt from `references/explorer-prompt.md` and have it return the sections in `references/explainer-prompt.md`.

That helper covers the question, or the slice you could not read. A second helper only when you can name the gap the first pass left.

## 3. Present

Present the explanation. Light edits for clarity or context from the conversation are fine. Do not substantially rewrite a helper's output. An explanation you wrote yourself is the output.

## Output format

The explanation uses the sections defined in `references/explainer-prompt.md`, dropping any that do not apply. Overview, Key concepts, How it works, Where things live, Gotchas.
