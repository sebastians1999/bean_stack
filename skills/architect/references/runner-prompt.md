# Architect sketch prompt

Use this as the discipline for the one sketch. The caller fills in the task and the Phase A grounding notes.

Read the **architect** skill in full first. Output one design package. Type sketch, function signatures, module map, and prose rationale shaped per [`rationale-template.md`](rationale-template.md).

- Caller's usage first. Write the usage and two or three real call sites before the types, then derive the type sketch from them. The usage is the spec. The two must agree, so reconcile the sketch to the usage.
- Data structures first. Get the core types right and the code becomes obvious. Trace each dominant access pattern through the proposed structure. If the answer is that a map, index, or cache can be added later, the structure is wrong.
- Interface depth. Compare the capability hidden behind the public surface with the size of that surface. Prefer a simple interface that pulls complexity into the callee. Do not put transport or wire types on the public API. Parse into domain types behind the interface.
- Shared state. If two actors might both write, ask what happens. If the answer is not "nothing", give each actor its own state and merge at the read boundary.
- Make boundaries visible. `not implemented` for bodies, pseudocode for tricky logic, and a doc comment where a public API needs an invariant the type cannot carry. A reader should trace data from input to output by reading types and signatures alone.
- Encode invariants in types. Prefer a type that cannot represent the bad state, then a runtime check, then prose.
- Validate at boundaries, trust types inside, per the **boundary-discipline** principle skill. Business logic as pure functions. The shell stays thin.
- Single source of truth per invariant. Derive instead of sync.
- Where an operation can run twice or crash halfway, make it converge to the same end state.
- Short call chains. If tracing the flow needs more than three files, flatten the hierarchy, per the **laziness-protocol** and **minimize-reader-load** principle skills.

Write the best sketch this task allows. A second sketch is a separate decision the architect skill makes, and only when this shape is genuinely contested.
