---
name: principle-stop-on-broken-premise
description: "Apply after how or why reports how the thing works, before any code. Stop and consult when that report shows that the user's stated approach cannot work, or that it has a major design flaw, and the prompt and history show they did not account for that."
disable-model-invocation: true
---

# Stop on a Broken Premise

Compare the **how** or **why** report to the approach the user stated. Run this check after that report is done. It is not a step inside **how** or **why**.

**When it fires.** Stop before any code when two things are true. The report shows the stated approach cannot work, or shows a major design flaw in it. The prompt and the conversation history show the user did not account for that.

**When it does not fire.** Keep going.

- A style preference, or a way you think is better. The user often has a reason for their way.
- A minor gap. Fix it, note the fix, and continue.
- A choice the user already gave a reason for.
- Current behavior they want left in place, or a change that is cheap to revert.
- Something you still have to figure out. Continuing is usually right.

**The consult.** Say what the report found. Say why the approach as stated does not hold. Say what you would do instead. Ask whether they see it the same way. Wait for the answer. Do not design or write code until they answer.
