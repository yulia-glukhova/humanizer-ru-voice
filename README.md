# humanizer-ru-voice

AI writing pattern remover with Russian language support and voice corpus calibration.

Fork of [blader/humanizer](https://github.com/blader/humanizer). Adds:

- **Russian AI patterns** — канцелярит, вводные конструкции, троица прилагательных, "в современном мире...", AI-превосходные степени
- **Voice corpus calibration** — load your own texts into `CORPUS.md` so the skill matches *your* voice, not just removes AI tells
- **Format-specific rules** — Telegram posts, carousel captions, Reels scripts, client reports
- **Voice drift detection** — separate check that edited text still sounds like you, not like a clean but voiceless rewrite

## How it works

| Step | What happens |
|------|-------------|
| 0 | Loads `CORPUS.md` and extracts your voice fingerprint (rhythm, tone, habits) |
| 1 | Detects content format (Telegram / carousel / Reels / report) |
| 2 | Scans for AI patterns — RU and EN — and rewrites affected passages |
| 3 | Checks for voice drift against your corpus |
| 4 | Runs format-specific final checks |
| 5 | Final anti-AI audit: catches what pattern-matching missed |

## Installation

### Claude Code

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/yulia-glukhova/humanizer-ru-voice.git ~/.claude/skills/humanizer-ru-voice
```

### Claude.ai (as a custom skill)

1. Download `SKILL.md` and `CORPUS.example.md`
2. Go to **Settings → Skills → + → Upload**
3. Upload both files

### Set up your voice corpus

```bash
cd ~/.claude/skills/humanizer-ru-voice
cp CORPUS.example.md CORPUS.md
```

Open `CORPUS.md` and paste 5–10 of your best texts: Telegram posts, report excerpts, carousel scripts. The more varied the examples, the better the calibration.

**Do not commit `CORPUS.md` to a public repo** — it contains your original texts. It's already in `.gitignore`.

## Usage

In Claude Code:

```
/humanizer-ru-voice [paste your text]
```

Or just ask Claude to edit your text — the skill triggers automatically when loaded.

## What's different from the original

| Feature | blader/humanizer | this fork |
|---------|-----------------|-----------|
| EN AI patterns | ✅ 24 patterns | ✅ same |
| RU AI patterns | ❌ | ✅ 5 categories |
| Voice corpus | ❌ | ✅ CORPUS.md fingerprinting |
| Voice drift check | ❌ | ✅ separate step |
| Format rules | ❌ | ✅ Telegram, carousels, Reels, reports |
| Corpus priority over examples | ❌ | ✅ inline examples don't override your voice |

## What this skill does NOT do

- Does not fact-check claims
- Does not change the author's conclusions or opinions
- Does not add information that wasn't in the original
- Does not enforce one "correct" style — it enforces *your* style from the corpus

## License

MIT — see [LICENSE](LICENSE).

Based on [blader/humanizer](https://github.com/blader/humanizer) by Siqi Chen, licensed under MIT.

---

Made by [Far & Wide IO](https://www.farandwide.io/)
