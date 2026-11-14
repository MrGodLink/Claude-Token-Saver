# Claude Token Saver

**English** | [Italiano](README.it.md)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green)](#)
[![Platform](https://img.shields.io/badge/platform-claude.ai%20%7C%20Claude%20Code-lightgrey)](#)

**Spend fewer tokens in your Claude conversations.** A skill for claude.ai and a ready-to-paste ruleset for Claude Code that make Claude answer tighter, repeat less and manage long chats better.

Companion project of [Claude-Token-Meter](https://github.com/MrGodLink/Claude-Token-Meter): the Meter shows how much context is left, the Saver helps you make it last longer.

---

## Overview

| | Where | What it changes |
|---|---|---|
| **Skill** (`skill/token-saver/`) | claude.ai and the apps | how Claude writes replies and uses tools |
| **Ruleset** (`claude-code/`) | Claude Code | same rules, to paste into `CLAUDE.md` |

## Features

- **Three modes** — *Saver* (default), *Ultra* (result only, no explanations), *Normal* (back to the standard style). Switch by just asking.
- **Tighter replies** — no greetings, no restating the question, no closing recap, proportional length.
- **No repeated content** — unchanged code or text is not printed again; only the modified parts are shown.
- **Fewer tool calls** — no web searches or file reads for things Claude already knows or has in context.
- **Fewer clarifying questions** — at most one, and only when essential.
- **Long-chat handling** — when less than ~30% of the context is left, Claude suggests a new chat and writes a handoff summary (max 150 words).
- **User tips** — a short list of habits that save tokens on your side (`references/consigli-utente.md`).

## Requirements

- **Skill:** a claude.ai account with Skills enabled (Settings → Capabilities).
- **Ruleset:** Claude Code. Nothing else to install.

## Installation

```
git clone https://github.com/MrGodLink/Claude-Token-Saver.git
cd Claude-Token-Saver
```

### 1. Skill for claude.ai

1. Upload [`releases/token-saver.skill`](releases/token-saver.skill) in Settings → Capabilities → Skills (or zip the `skill/token-saver/` folder and upload the `.zip`).
2. Open a new chat and say "save tokens" or "short replies".

**To keep the mode always on**, Claude loads skills only when it considers them useful. Paste this in Settings → Profile → personal preferences (new chats only):

```
Always save tokens: answer directly with no greetings, no restating my question and no closing recap. Keep length proportional to the question. Minimal formatting. Never reprint unchanged code or text, show only what changed. At most one clarifying question, only if essential. Do not use tools for things you already know. If I say "ultra", give only the result.
```

### 2. Ruleset for Claude Code

Copy the content of [`claude-code/token-saver-CLAUDE.md`](claude-code/token-saver-CLAUDE.md) into your project `CLAUDE.md` (or `~/.claude/CLAUDE.md` for all projects).

## Usage

| You say | Result |
|---|---|
| "save tokens" / "risparmia token" | Saver mode on |
| "ultra" / "only the result" | Ultra mode: telegraphic replies |
| "normal" / "explain better" | back to the standard style |
| "how can I save tokens?" | 2-3 relevant tips for your side |

### Customization

| What | Where |
|---|---|
| Rules and modes | `skill/token-saver/SKILL.md` |
| Low-context threshold (30%) | "Gestione del contesto" section in `SKILL.md` |
| Handoff summary length (150 words) | same section |
| User tips | `skill/token-saver/references/consigli-utente.md` |

> The skill text is written in Italian (Claude follows it in any language you chat in). Edit `SKILL.md` before uploading to translate it.

## Architecture

```
Claude-Token-Saver/
├── skill/
│   └── token-saver/
│       ├── SKILL.md                    # the skill (instructions for Claude)
│       └── references/
│           └── consigli-utente.md      # tips for the user, loaded on demand
├── claude-code/
│   └── token-saver-CLAUDE.md           # ruleset for CLAUDE.md
├── releases/
│   └── token-saver.skill               # ready-to-upload package
├── LICENSE
├── README.md
└── README.it.md
```

## Limitations

- It mainly reduces **Claude's output** and tool use. What is already in the chat keeps counting until you open a new conversation.
- The skill itself takes a little context when it triggers: it pays off on long or repetitive chats, less on a single question.
- Token estimates are approximate (about 4 characters = 1 token).
- Shorter replies are a trade-off: if you need depth, say "normal" or "explain better".
- Not extensively tested: feedback and issues are welcome.

## Privacy and responsible use

- Plain text instructions: nothing is sent anywhere by this project and there is no code to run.
- This is an independent community project, not affiliated with or endorsed by Anthropic.

## Credits

Created by **Raffaele Catapano** — [github.com/MrGodLink](https://github.com/MrGodLink)

If you reuse, modify or redistribute this project, please keep the copyright notice and credit the original author, as required by the MIT License.

Bug reports and ideas are welcome in the [issue tracker](https://github.com/MrGodLink/Claude-Token-Saver/issues).

## License

Released under the MIT License — see [LICENSE](LICENSE).
