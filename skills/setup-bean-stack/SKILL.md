---
name: setup-bean-stack
description: Configure which model each Bean Stack subagent role uses. Detects your available models and writes an always-applied rule that overrides the defaults. Use for /setup-bean-stack, "configure bean stack models", or changing a subagent's model.
---

# Setup Bean Stack

Write `~/.cursor/rules/bean-stack-models.mdc`, an always-applied rule that sets the model for each subagent role. The main chat model is the user's pick in the model picker. This skill does not set it.

## Steps

### 1. Detect available models

Enumerate the model slugs you can pass to a `Task` subagent in this session. If you cannot detect any, ask the user to paste the slugs they have. Never write a real slug you have not confirmed is available. `inherit-parent` is always valid.

### 2. Load current state

Start from the Models table in the **sebastian-mode** skill. It names every role and its default. If `~/.cursor/rules/bean-stack-models.mdc` exists, read it and treat its values as the current choices. Drop a line whose role is not in the table.

### 3. Show the roles and ask

Show every role with its current model and what spawns it. Mark a slug that is not in the detected set as needing a choice. Ask once with AskQuestion: accept all, or change specific roles. For each role the user changes, offer the detected slugs plus `inherit-parent`, which runs that role on the parent chat model.

### 4. Validate

Every real slug written must be in the detected set. If a chosen slug is not available, ask again for that role.

### 5. Write the rule

Overwrite the whole file so a rerun gives the same result. One line per role, with the role names from the table. Shape:

```
---
description: Bean Stack per-role subagent models (overrides the sebastian-mode defaults)
alwaysApply: true
---
# One line per role. Delete a line to fall back to the default. `inherit-parent` runs the role on the parent chat model.
implementer: grok-4.7-xhigh
comment pass: composer-2.5
how and why: composer-2.5
architect helper: grok-4.7-xhigh
automate-me mining: grok-4.7-xhigh
trail reviewer: composer-2.5
```

### 6. Confirm

Tell the user the rule was written and that it applies to new chats. A rerun of `/setup-bean-stack` updates it. In a harness that does not load Cursor rules, the defaults in the Models table apply.
