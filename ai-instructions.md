# AI Chat Engine — Instructions
<!-- version: 1.0 -->

This project is a file-based chat engine. Conversations live in `.md` files under `chats/`, are version-controlled with git, and the AI model can be swapped freely because the format is model-agnostic.

---

## Chat Format

Each chat file follows a strict turn-based structure:

```
## ME

{user writes here}

## AI ({make}/{model}) @ {YYYY-MM-DD}

> {AI response, every line prefixed with > so it renders as a blockquote}

## ME

{next user turn — always left blank by the AI as an invitation to write}
```

### Rules for the AI

1. **Read the file** on every nudge ("you go", "go ahead", etc.)
2. **Find the last `## ME` block** — that is the message to respond to.
3. **Append** your response directly below it. Never edit earlier turns.
4. **Header format:** `## AI ({make}/{model}) @ {YYYY-MM-DD HH:MM}` — use today's date and current time.
5. **Quote every line** of your response with `>` (blockquote syntax).
6. **End every response** with a blank `## ME` block on a new line so the user can write immediately. If the user's name is known from `context/user.md`, personalise it: `## ME (Laszlo)` instead of `## ME`.
7. **Code snippets:** create a `snippets/` folder next to the chat file if it doesn't exist. Save each snippet as its own file (`snippets/description.ext`). Reference it in your response with a relative link.

### Example

```markdown
## ME (Laszlo)

Write a hello world in Python.

## AI (Anthropic/claude-sonnet-4-6) @ 2026-06-18 09:50

> Sure! I've saved the snippet to [snippets/hello.py](snippets/hello.py).
>
> It prints "Hello, world!" to stdout — nothing fancy, just the classic.

## ME (Laszlo)

```

---

## Context Files

At the start of any conversation, read all context files that exist. They are optional — missing files are silently skipped.

```
context/
  user.md                        # who the user is, their role, preferences, and personality/style prefs
chats/
  projects/
    <project-name>/
      base.md                    # one folder per project; base.md holds project context
```

Each file is a Q&A — a question as a heading, the user's answer below. Use the answers to tailor every response.

**Important:** if a question has no answer (blank or only an HTML comment), skip it entirely. Do not infer, guess, or hallucinate an answer. Context files are purely additive — an unanswered question has zero effect.

---

## Project Structure

```
context/
  user.md
chats/
  initial.md                     # bootstrap / onboarding chat
  <topic>/                       # sub-folders for topic groupings
    <chat>.md
  projects/
    <project-name>/
      base.md                    # project context
  snippets/                      # code snippets referenced from chat files
```

---

## Swapping Models

To use a different model, point it at any chat file and follow the same format. The `## AI ({make}/{model})` header records which model wrote which turn — useful when you compare outputs across models in the same file.
