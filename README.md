# humanizer-ru-voice

Removes AI writing patterns and calibrates text to match the author's voice. Supports Russian and English.

Based on [blader/humanizer v2.2.0](https://github.com/blader/humanizer) (Wikipedia "Signs of AI writing") with additions for Russian-language AI patterns, format-specific rules (Telegram, carousels, Reels, client reports), and voice corpus calibration.

## Two versions

This skill works in two different Claude environments. They have **identical content** but different `allowed-tools` in the YAML frontmatter because the platforms use different tool names.

| | Claude AI (claude.ai) | Claude Code (CLI) |
|---|---|---|
| **Folder** | `claude-ai/` | `claude-code/` |
| **Tools** | `read_file` | `Read, Write, Edit, Grep, Glob, AskUserQuestion` |
| **Install method** | Upload as custom skill in claude.ai Settings | Add to `.claude/skills/` in your project |

## Installation

### Claude AI (claude.ai / web & app)

1. On Web Version Go to **Settings > Profile > Custom skills** 
2. On Desctop Version Go to **Customize > Skills > Add skill**
2. Click **Add skill**
3. Copy the contents of `claude-ai/SKILL.md` into the skill editor
4. (Optional) Also upload `CORPUS.md` with examples of your writing style

### Claude Code (CLI)

1. In your project, create the skill directory:

```bash
mkdir -p .claude/skills/humanizer-ru-voice
```

2. Copy the skill file:

```bash
cp claude-code/SKILL.md .claude/skills/humanizer-ru-voice/SKILL.md
```

3. (Optional) Add your voice corpus:

```bash
cp CORPUS.md .claude/skills/humanizer-ru-voice/CORPUS.md
```

4. The skill will be automatically picked up by Claude Code on next run.

## Voice corpus (CORPUS.md)

Both versions support an optional `CORPUS.md` file placed in the same directory as `SKILL.md`. This file should contain 5-10 examples of your real writing (blog posts, Telegram posts, client emails) so the humanizer can match your specific voice, not just remove AI patterns.

Without a corpus, the skill removes AI tells and applies general good-writing principles. With a corpus, it additionally calibrates rhythm, tone, and structural habits to match your voice.

## What it covers

**5 Russian-specific patterns (RU-1 through RU-5):**
Канцелярит, AI-превосходные степени, обобщающие финалы, "мы живём в мире где...", троица прилагательных

**24 English patterns (EN-1 through EN-24):**
Significance inflation, notability emphasis, superficial -ing analyses, promotional language, vague attributions, "challenges and future prospects" sections, AI vocabulary, copula avoidance, negative parallelisms, rule of three, synonym cycling, false ranges, em dash overuse, boldface overuse, inline-header lists, Title Case, emojis in structure, curly quotes, chatbot residue, knowledge-cutoff disclaimers, sycophantic tone, filler phrases, excessive hedging, generic positive conclusions

**Plus:** personality/soul injection, format-specific checks (Telegram/carousel/Reels/client report), two-pass anti-AI audit, voice drift detection.

## Credits

- EN patterns: [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) via [blader/humanizer](https://github.com/blader/humanizer)
- RU patterns, format rules, voice corpus system: original work


---

Made by [Far & Wide IO](https://www.farandwide.io/)
