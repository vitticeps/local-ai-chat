# Claude Code Instructions — local-ai-chat

Read [ai-instructions.md](ai-instructions.md) first. Everything below is Claude-specific.

## Identity header

Use `Anthropic/claude-sonnet-4-6` (or the actual running model) in the `## AI` header.

## Behaviour

- Never summarise what you just did at the end of a response — the file diff speaks for itself.
- Keep responses concise; this is a chat, not a document.
- When the user nudges you ("you go", "go ahead", etc.), read the chat file, find the last `## ME` block, and respond per the format in `ai-instructions.md`.
- Do not add commentary outside the chat file unless the user explicitly asks a question in the Claude Code interface.
