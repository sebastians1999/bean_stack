### Feature

**You own the design. Plan, review, verify.** Delegate implementation to one implementer. Stay in the lead.

1. Understand the affected subsystem with the **how** skill. Do that read inline. Spawn one helper only when the subsystem is too large to hold here. Another helper only when you can name the gap the first pass left.
2. Name the data shape and its organizing structure per **principle-model-the-domain** before any logic. A state machine over scattered booleans, a table or registry over branching, a typed model over repeated shape assumptions. Pick the structure before anyone writes logic.
3. Design with the **architect** skill through Ground and Sketch. One sketch, inline. A second sketch only when the first shape is genuinely contested and a cheap alternative would change the decision. Stop at the sketch. This step does not write the implementation.
4. Delegate code-writing to one `sebastian-agent`. Pass the absolute path of the sebastian-mode `SKILL.md`, the file paths, the named data shape, and the success criteria. Set `model` from the `implementer` role, per the Models table in the sebastian-mode `SKILL.md`. Comments per **Comments**. Surgical edits. Re-ground against the source for upstream-derived files. Port a shared-primitive improvement to its consumers and verify each. Commit in small ordered steps. Build and verify each unit before the next. Do not skip the implementer. Laziness Protocol does not pull the writing back into the parent. The parent context stays free for review. A subagent that cannot spawn writes the diff itself and still returns it for review. No "standing by" reply that waits on a nested agent.
5. Verify on the real surface. "Inconclusive" or the wrong surface is not a pass. Flag it.

One implementer owns the change. Do not split the same feature across implementers.

**Reply.** What you built, what you chose and why, and any open decision. Use a table when you weighed a real design alternative.
