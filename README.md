# Bean Stack

Bean Stack is Sebastian Schmülling's agent skill set, forked from [pstack](https://github.com/cursor/plugins/tree/main/pstack) 0.15.25 by Lauren Tan. pstack is MIT. This repo keeps that license and the copyright notice in `LICENSE`.

`/sebastian-mode` is the entry point for implementation work. The agent understands the subsystem, names the data shape, sketches the design, hands the code to one implementer, and verifies on the real surface. `how` and `architect` run in the parent agent unless one helper is needed.

## Install in Cursor

This checkout is the only copy. Cursor reads skills from `~/.cursor/skills` and subagents from `~/.cursor/agents`. Point those at this repo, using its absolute path:

```
ln -sfn /absolute/path/to/bean_stack/bean-stack/skills ~/.cursor/skills
mkdir -p ~/.cursor/agents
ln -sfn /absolute/path/to/bean_stack/bean-stack/agents/bean-agent.md ~/.cursor/agents/bean-agent.md
ln -sfn /absolute/path/to/bean_stack/bean-stack/agents/comment-sicko.md ~/.cursor/agents/comment-sicko.md
```

Restart Cursor, or run Developer: Reload Window. Turn on Settings → Agents → Sync Skills for Cloud Agents so cloud agents receive the skills.

Do not also keep `~/.cursor/plugins/local/bean_stack`. Cursor skips a plugin symlink whose target sits outside that folder, so the plugin cannot be this repo. A copied plugin would load the same skills a second time.

Start a task with `/sebastian-mode`.

Run `/setup-bean-stack` once to choose a model per subagent role. It writes `~/.cursor/rules/bean-stack-models.mdc`. Without that file, the defaults in the Models table of `bean-stack/skills/sebastian-mode/SKILL.md` apply. The implementer, the architect helper, and the automate-me miner run on `grok-4.7-xhigh`. The comment pass, the how and why subagents, and the trail reviewer run on `composer-2.5`. The main chat model is whatever you pick in Cursor.

## Install from the marketplace

Import this repository in Dashboard → Plugins & MCPs → Add Marketplace → Import from Repo. Cursor reads `.cursor-plugin/marketplace.json` and loads the plugin in `bean-stack/`. The plugin name is `bean-stack`. Turn on Enable Auto Refresh, with the Cursor GitHub App installed on this repo, so a push updates the marketplace.

## Install for other agents

Other harnesses read `bean-stack/plugin.json` and the `bean-stack/skills/` tree. Point the agent at this checkout and have it read `bean-stack/skills/sebastian-mode/SKILL.md` before implementation work. When the harness can spawn subagents, the code-writing delegate is `bean-agent`. When it cannot, the parent agent writes the code and still follows the playbook.

## License

MIT. Copyright (c) 2026 Lauren Tan.
