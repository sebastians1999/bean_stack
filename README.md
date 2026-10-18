# Bean Stack

Bean Stack is Sebastian Schmülling's agent skill set, forked from [pstack](https://github.com/cursor/plugins/tree/main/pstack) 0.15.25 by Lauren Tan. pstack is MIT. This repo keeps that license and the copyright notice in `LICENSE`.

`/sebastian-mode` is the entry point for implementation work. The agent understands the subsystem, names the data shape, sketches the design, hands the code to one implementer, and verifies on the real surface. `how` and `why` each start in one subagent and never use more than two. `architect` runs in the parent agent unless one helper is needed.

## Install in Cursor

Cursor loads `.cursor-plugin/plugin.json`. That manifest points at `skills/` and `agents/`.

Copy this repo to `~/.cursor/plugins/local/bean_stack`. Restart Cursor, or run Developer: Reload Window. Open Customize and confirm Bean Stack is listed. Copy the directory into that folder. A symlink whose target sits outside `~/.cursor/plugins/local` is skipped. On an Enterprise team, an admin turns on Allow Local Plugin Imports before that folder loads. A marketplace plugin with the same name takes precedence over the local copy.

Start a task with `/sebastian-mode`.

Run `/setup-bean-stack` once to choose a model per subagent role. It writes `~/.cursor/rules/bean-stack-models.mdc`. Without that file, the defaults in the Models table of `skills/sebastian-mode/SKILL.md` apply. The implementer, the architect helper, and the automate-me miner run on `grok-4.7-xhigh`. The comment pass and the how and why subagents run on `composer-2.5`. The main chat model is whatever you pick in Cursor.

## Install for other agents

Other harnesses read the root `plugin.json` and the `skills/` tree. Point the agent at this checkout and have it read `skills/sebastian-mode/SKILL.md` before implementation work. When the harness can spawn subagents, the code-writing delegate is `sebastian-agent`. When it cannot, the parent agent writes the code and still follows the playbook.

The root manifest name is `bean_stack`, the same as this repo. The Agent Plugins 1.0 name pattern allows lowercase letters, digits, dots, and hyphens. A strict validator will reject the underscore. The Cursor manifest is a separate file and carries the display name Bean Stack.

## License

MIT. Copyright (c) 2026 Lauren Tan.
