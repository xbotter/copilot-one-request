# CopilotOneRequest

A GitHub Copilot CLI skill that teaches Copilot to always ask the user for their next instruction — especially after completing a task.

## Skill: `asking-user-next-steps`

**Core principle:** Copilot should never go silent after finishing a task. It should always use the `ask_user` tool to wait for the user's next instruction.

## Usage

Install this skill by placing `SKILL.md` in one of:
- Your project's root directory (for project-scoped sharing)
- `~/.agents/skills/asking-user-next-steps/SKILL.md` (for personal use)

Once loaded, the skill instructs Copilot to:
1. Use `ask_user` (structured form input) instead of plain text questions when in Copilot CLI
2. Always follow up after completing any task with a prompt for next steps
3. Never silently end a session

## Files

- `SKILL.md` — The skill definition
