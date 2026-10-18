# Gap explorer prompt template

Build the second subagent's prompt from this template. Fill in the placeholders. Paste the output sections from `explainer-prompt.md` into the prompt.

---

A first explorer already explained this subsystem and named a gap it could not close. Don't re-explore what it covered. Focus on the gap and go deep.

## Question

> {QUESTION}

## First explanation

{FIRST_EXPLANATION}

## The gap

{EXPLORATION_ANGLE}

## Output

Return the revised explanation in the sections from the explanation spec. Merge what you found into the first explanation, and correct it where the code says otherwise. Name the files you read for the gap. End with any open questions you still could not close.
