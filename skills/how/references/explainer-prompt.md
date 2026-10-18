# Explanation sections

Write an architectural explanation for a senior engineer. Use this structure. Drop a section that does not apply.

## Original question

> {QUESTION}

## Notes

{NOTES}

Notes may be empty when you read the code yourself. When a helper passed findings, reconcile them with the code. Merge overlapping descriptions, resolve a contradiction by checking the code, and combine the slices into one picture.

## Instructions

Write an explanation a senior engineer unfamiliar with this area could read and walk away with a working mental model.

You may read the codebase to check a detail or fill a gap. Use Read, Grep, and Glob. When the notes already cover the question, do not re-explore from scratch.

## Output format

### Overview

One or two paragraphs. What this thing is, what it does, and why it exists. Someone should be able to read just this and decide whether to keep reading.

### Key concepts

The important types, services, or abstractions needed to follow the rest. Brief definitions.

### How it works

The core of the explanation, and the longest section. Walk through the flow. What triggers it, what happens step by step, where data goes, and what the decision points are.

Use prose. Reference specific files and functions so the reader knows where to look. Do not dump large code blocks unless a snippet is essential to a point.

When the flow involves multiple components, or data transforming through stages, include a diagram. Use mermaid for a sequence, flowchart, or component graph. Use ASCII art for a simpler relationship. A diagram should clarify. If prose covers the flow, skip the diagram.

### Where things live

A brief file and directory map. Just the paths someone would open to start working here.

### Gotchas

Non-obvious behavior, surprises, and pitfalls. Skip this section when there is nothing worth calling out.

## Communication style

- Use concrete language. Say "the `UserService` calls `AuthClient.refresh()`" when that is what happens.
- When something is complex, explain why it is complex.
- When something is simple, do not pad it.
- Use an analogy only when it teaches the structure. Otherwise skip it.
- Name a gap you could not close.
