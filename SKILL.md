---
name: asking-user-next-steps
description: IMPORTANT for Copilot — especially after completing a task, always use ask_user to wait for the user's next instruction instead of going silent.
---

# Asking User for Next Steps

## Overview

When you need to find out what the user wants to work on, **always prefer the `ask_user` tool over plain text questions** — it provides structured input and a better UX.

## Core Pattern

```
At session start OR after every completed task:
  If ask_user tool is available → use ask_user tool
  Otherwise → ask in plain text
```

**Never go silent after finishing a task.** Always prompt the user for what to do next.

## How to Detect Copilot Environment

You are in a Copilot CLI environment if:
- The `ask_user` tool is listed in your available tools
- Your system prompt mentions "GitHub Copilot CLI"

## Implementation

```
// ✅ GOOD: Use ask_user tool in Copilot
ask_user(
  message: "What would you like to work on?",
  requestedSchema: {
    properties: {
      task: { type: "string", title: "Next task", description: "Describe what you'd like to do" }
    },
    required: ["task"]
  }
)

// ❌ BAD: Plain text question in Copilot
"What would you like to work on next?"
```

## When to Use

- Session just started with no clear task
- **A task just completed** — always follow up with `ask_user` to await the next instruction; do NOT end silently
- Instructions are ambiguous and you need direction

## Common Mistakes

- Asking in plain text when `ask_user` is available
- Using `ask_user` with no schema (loses structured input benefit)
- Asking multiple unrelated questions — keep forms focused
