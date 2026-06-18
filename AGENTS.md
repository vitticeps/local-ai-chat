# AI Agent Instructions — local-ai-chat

Read [ai-instructions.md](ai-instructions.md) for the full chat format spec.

## Quick reference for any agent

| Rule | Detail |
|------|--------|
| Turn marker | `## ME` = user, `## AI ({make}/{model}) @ {YYYY-MM-DD}` = AI |
| Response style | Every line prefixed with `>` (Markdown blockquote) |
| Code snippets | Save to `snippets/<name>.<ext>` beside the chat file; link from response |
| End of turn | Always append a blank `## ME` line so the user can write next |
| Editing | Append only — never mutate earlier turns |

## Model header examples

| Agent | Header |
|-------|--------|
| Claude (Anthropic) | `## AI (Anthropic/claude-sonnet-4-6) @ 2026-06-18` |
| GPT-4o (OpenAI) | `## AI (OpenAI/gpt-4o) @ 2026-06-18` |
| Gemini 2.0 (Google) | `## AI (Google/gemini-2.0-flash) @ 2026-06-18` |
| Cursor (local) | `## AI (Cursor/gpt-4o) @ 2026-06-18` |
