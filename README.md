# local-ai-chat

A file-based chat engine where conversations live in plain Markdown files, the AI model is swappable, and everything is version-controlled with git.

## The idea

Most AI chat tools lock your conversations into a proprietary UI. Here, every conversation is a `.md` file you own. You can read it, edit it, diff it, branch it, and open it in any editor. Swap the model and the conversation just keeps going — the format is the same regardless of who's on the other end.

## How it works

Conversations use a simple turn-based format:

```markdown
## ME

Your message goes here.

## AI (Anthropic/claude-sonnet-4-6) @ 2026-06-18 09:52

> AI response here, rendered as a blockquote.

## ME
```

- `## ME` marks your turn.
- `## AI ({provider}/{model}) @ {timestamp}` marks the AI's turn.
- The `>` prefix makes responses render as blockquotes in any Markdown preview.
- Code snippets are saved as separate files in a `snippets/` folder alongside the chat.

To continue a conversation, write under the last `## ME` block and nudge your AI tool. With Claude Code, just say "you go".

## Project structure

```
chats/
  initial.md          # getting started / meta chat
  <topic>/            # group chats by topic
    <name>.md
  snippets/           # code snippets referenced from chat files
ai-instructions.md    # model-agnostic format spec
CLAUDE.md             # Claude Code specific instructions
AGENTS.md             # quick-reference for any AI agent
.cursorrules          # Cursor-specific instructions
```

## Why bother?

- **You own the data.** Files, not a database. Copy them, back them up, read them offline.
- **Git-friendly.** Diffs are meaningful. Branch for experiments, merge the good ones.
- **Model-agnostic.** The `## AI ({provider}/{model})` header records who wrote what. Run the same chat through GPT, Claude, and Gemini and compare side by side.
- **Editor-native.** Any editor that renders Markdown gives you a readable chat. No special tooling required.

> [!TIP]
> If you push this repo to GitHub, make it **private** or add relevant folders/files to `.gitignore` — your `context/` files may contain personal information.

## Getting started

1. Clone this repo.
2. Open any `.md` file under `chats/` in your editor.
3. Write a message under `## ME`.
4. Point your AI tool at the file and tell it to respond (e.g. `you go` in Claude Code).
5. Commit the result.

