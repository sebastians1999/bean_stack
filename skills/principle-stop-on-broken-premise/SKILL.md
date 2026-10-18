---
name: principle-stop-on-broken-premise
description: "Apply after how or why reports how the thing works, and before any code. Stop before any code only when the prompt and the conversation history show the user did not account for what the report found. The report must show that the stated approach cannot work, or that it has a major design flaw."
disable-model-invocation: true
---

# Stop on a broken premise

Compare the how or why report to the approach the user stated. Run this check after that report is done. Leave the how skill and the why skill unchanged.

**When to stop.** Stop before any code only when the prompt and the conversation history show the user did not account for what the report found. The report must show that the stated approach cannot work, or that it has a major design flaw.

**When to continue.** Keep going.

- Continue when the disagreement is about style. Continue when you prefer another way. The user often has a reason for their way.
- Fix a minor gap, note the fix, and continue.
- Keep a choice the user already gave a reason for.
- Leave current behavior in place when the user wants that. Continue when the change is cheap to revert.
- Continue when you still have to learn how the thing works. Run this check only after the how or why report is done.

**What to tell the user.** Say what the report found. If the approach cannot work, say why. If the finding is a design flaw, say why you should not build that approach as stated. Say what you would do instead. Ask whether they see it the same way. Wait for the answer. Do not design or write code until they answer.
