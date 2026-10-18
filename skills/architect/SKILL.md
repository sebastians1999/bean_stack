---
name: architect
description: "Sketch types, signatures, and module structure before code, then stay in the loop while implementation fills in. Use for /architect, 'architect this', 'design this', or non-trivial work where jumping to code would lock in the wrong shape."
disable-model-invocation: true
---

# Architect

Sketch types, function signatures, class shapes, and module boundaries with `not implemented` bodies and pseudocode. Write one sketch, then fill in code against it.

## Start

Open a todolist with one entry per phase before starting.

1. Ground
2. Sketch
3. Agree
4. Implement
5. Scrap

## Phase A: Ground the problem

Build a real mental model of every system the new code touches. Run the **how** skill over the relevant subsystems. Naming a file is not grounding. Produce the architectural explanation `how` prescribes. If the design redefines ownership or layering, also run the **why** skill on the existing shape so the rationale becomes a constraint, not a guess.

Skip Phase A only when the work is genuinely greenfield with no surrounding system to integrate.

## Phase B: Sketch

Write one sketch in this agent. When the sketch does not fit here, spawn one helper with `subagent_type: generalPurpose` and set `model` from the `architect helper` role, per the Models table in the **sebastian-mode** skill. Use `references/runner-prompt.md` as the discipline for that sketch. Screen it against [`references/design-red-flags.md`](references/design-red-flags.md) before treating it as the design.

Assume the next contributor is an agent that sees only the files it opened, copies the nearest example, and takes the shortest path that compiles. Prefer the design where a change that looks right from one file is right for the whole repo.

Compare the sketch with one cheaper alternative only when the first shape is genuinely contested and that alternative would change the decision. Weigh them yourself, in this agent. Do not spawn a panel.

Prefer the design that hides more complexity behind a smaller, simpler public surface. A rich interface can keep call chains short by concentrating capability.

The rationale's Decision section records why this shape won. When you wrote no second sketch, say what constraint made this the shape.

## Phase C: Agree (opt-in)

**Default.** Proceed with the sketch. No human checkpoint.

Opt in to a checkpoint when the invoker explicitly asks to stop and show the design before implementing. Then surface the sketch and pause for sign-off.

The sketch can ship as its own commit, as the "scaffold first" mode of the **foundational-thinking** principle skill.

If the human pushes back on the shape (in a checkpoint or after the fact), treat that as Phase A evidence. Re-ground and re-run Phase B before writing more code.

When a playbook owns implementation, stop this skill at the end of Phase B, or after Phase C if a checkpoint was requested. The playbook writes the code.

## Phase D: Implement against the sketch

Replace `not implemented` bodies with code, and pseudocode with logic. The sketch is the contract. Deviations from it are signal to surface. If a function needs a parameter the sketch did not anticipate, ask whether the sketch was wrong, the requirement was missed, or the implementation is overreaching.

Under `/sebastian-mode`, the feature playbook delegates this phase to one `bean-agent`. A direct `/architect` invocation writes the code here.

## Phase E: Scrap when the architecture is wrong

If implementation keeps producing friction the sketch cannot absorb, throw the sketch out. Do not bolt fixes onto a wrong design, per the **fix-root-causes** principle skill.

The signal is a pattern, not a single instance. Tells:

- The same shape of workaround appearing repeatedly across unrelated code.
- Multiple unrelated edge cases that all need special-case branches.
- Types that need escape hatches (`any`, casts, optional fields always set in practice) to compile.
- The "we need a lock" reflex when the sketch said the state was not shared.
- Callers having to know the abstraction's internal rules to use it.
- Two or more independent Phase D deviations of the same shape across the implementation.

Use judgment. A few edge cases do not condemn an architecture. Some problems are legitimately complex. Complexity in the data is not complexity in the design.

When you scrap:

1. Re-run the **how** skill over what has been built.
2. Redesign as if the new constraints had been there on day one.
3. Subtract before adding, per the **subtract-before-you-add** principle skill. The new sketch should be smaller than the old one before it grows.
4. Return to Phase B and write one new sketch.

## Outputs

The caller's usage is written first and the type sketch derived from it. One file with new types and signatures for small changes. Module map plus type definitions for larger work. The rationale ships alongside, shaped per `references/rationale-template.md`, including the usage sketch and the decision.
