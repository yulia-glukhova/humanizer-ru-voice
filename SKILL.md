---
name: humanizer-ru-voice
version: 1.0.0
description: >
  Removes AI writing patterns and calibrates text to match the author's voice.
  Use when editing Telegram posts, carousel captions, Reels scripts, or client reports
  to make them sound human and on-brand — not like ChatGPT output.
  Supports Russian and English. If a CORPUS.md file is present in this skill directory,
  read it first to extract the author's voice fingerprint before editing.
allowed-tools: read_file
---

# humanizer-ru-voice

A writing editor that removes AI tells and calibrates output to the author's voice.
Based on [blader/humanizer](https://github.com/blader/humanizer) with additions for:
- Russian-language AI patterns
- Format-specific rules (Telegram, carousels, Reels, client reports)
- Voice corpus calibration

---

## Step 0 — Load corpus (if available)

Before editing anything, check if `CORPUS.md` exists in this skill's directory.
If it does, read it and extract the author's voice fingerprint:

- Typical sentence length and rhythm
- How lists are used (or avoided)
- Opening patterns (does the author start with a hook, a question, a statement?)
- What the author does NOT do (no em dashes? no bullet lists? no "важно отметить"?)
- Tone markers: formal/casual, distance from reader, use of "я" / "мы" / "ты"
- Signature phrases or structural habits

Keep this fingerprint active throughout the edit. Voice drift is a failure even if no AI patterns are triggered.

---

## Step 1 — Detect format

Identify which format you're editing and apply the relevant rules below alongside the universal ones.

**Telegram post** — punchy, personal, no corporate tone. Short paragraphs. Емкость важнее полноты.
**Carousel** — each slide = one idea. No "in conclusion" slides. Hooks on slide 1, payoff on last.
**Reels script** — spoken rhythm. Read aloud — if it sounds like a press release, rewrite.
**Client report** — precise, no fluff, no hedging with empty adjectives. Facts > adjectives.

---

## Step 2 — Universal AI pattern check

Scan for all of the following and rewrite affected passages.

> **Note:** The ❌/✅ examples below illustrate the *direction* of the fix, not the target style.
> Target style is defined solely by CORPUS.md. If a corpus is loaded, adapt all rewrites
> to match its rhythm and tone — not the phrasing of these examples.

### RU patterns (Russian-specific AI tells)

**Канцелярит и вводные конструкции**
Words to watch: важно отметить, стоит подчеркнуть, необходимо учитывать, следует отметить, хотелось бы обратить внимание, в данном контексте, данный/данная/данное (вместо «этот»), осуществляет, является, в рамках, в целях, посредством
Fix: Cut entirely or replace with direct statement.

> ❌ Важно отметить, что данный подход осуществляет переход к новой модели.
> ✅ Подход меняет модель.

**AI-превосходные степени**
Words to watch: уникальный, революционный, передовой, инновационный, ключевой, значимый, актуальный, эффективный (без доказательств)
Fix: Delete or replace with a specific fact.

> ❌ Это уникальное и инновационное решение для современного бизнеса.
> ✅ Решение сокращает время онбординга с 3 недель до 4 дней.

**Обобщающие финалы**
Phrases to watch: таким образом, подводя итог, в заключение, в конечном счёте, в современном мире, в эпоху цифровизации
Fix: End with a concrete statement or a question, not a summary bow.

**"Мы живём в мире, где..."**
Problem: AI любит открывать текст с глобального контекста.
Fix: Start with конкретным фактом или наблюдением.

> ❌ В современном мире маркетинг переживает трансформацию.
> ✅ ChatGPT отвечает на 10 миллиардов запросов в месяц. Часть из них — про твой бренд.

**Троица прилагательных**
Problem: AI стекирует по три синонима для усиления.
Words to watch: быстрый, удобный и надёжный / точный, структурированный и понятный
Fix: Оставь одно — самое точное.

---

### EN patterns (English AI tells — from blader/humanizer)

**Significance inflation**
Words to watch: stands as, serves as, is a testament to, is a reminder that, underscores, highlights, reflects broader, symbolizing, contributing to, setting the stage for, key turning point, evolving landscape, indelible mark
Fix: State the fact directly without the framing.

> ❌ This update stands as a testament to the team's commitment to excellence.
> ✅ The team shipped it on time with zero regressions.

**Promotional language**
Words to watch: boasts, vibrant, rich (figurative), profound, groundbreaking, renowned, breathtaking, stunning, nestled, in the heart of, must-visit, seamless, robust, leverage, innovative
Fix: Replace with specific, verifiable description.

**Superficial -ing analyses**
Problem: Tacking participial phrases to add fake depth.
> ❌ The product improves workflows, enhancing team productivity and fostering collaboration.
> ✅ The product cuts meeting prep time by 40%.

**Vague attribution**
Problem: "Studies show", "experts say", "research suggests" with no citation.
Fix: Name the source or delete the claim.

**Em dash overuse**
Problem: LLMs use em dashes to signal punchy emphasis — constantly — even when unnecessary.
Fix: Use period or restructure. One em dash per paragraph maximum.

**Rule of three**
Problem: AI defaults to three-item lists even when two or four would be more natural.
> ❌ Fast, flexible, and powerful.
> ✅ Fast and flexible. (If only two things matter, say two.)

**AI vocabulary**
Words to watch: delve, pivot, navigate, tapestry, mosaic, multifaceted, nuanced (overused), holistic, synergy, paradigm shift, game-changer, unlock, supercharge, elevate
Fix: Replace with plain or specific language.

**Copula avoidance**
Problem: AI replaces "is/are" with elaborate constructions to sound sophisticated.
> ❌ The platform functions as a central hub for team communication.
> ✅ The platform is where the team communicates.

**Negative parallelism**
Problem: "Not X, but Y" constructions used for false profundity.
> ❌ This isn't just about features. It's about transformation.
> ✅ (Delete entirely or replace with a specific claim.)

**Bold header lists**
Problem: AI formats prose as **Header:** explanation lists.
Fix: Convert to flowing sentences unless the format genuinely requires a list.

**Excessive conjunctive adverbs**
Words to watch: furthermore, moreover, additionally, in addition, consequently, therefore (when used as filler, not logical connectors)
Fix: Cut or restructure to show logical flow without the signpost.

---

## Step 3 — Voice drift check (if corpus loaded)

After removing AI patterns, compare against the voice fingerprint from Step 0.

Ask: **"Does this sound like [author] or does it sound like a clean, voiceless version of [author]?"**

Flags to check:
- Sentence rhythm matches corpus? (длина, ритм чередования)
- Degree of first-person presence matches? (автор пишет "я" или избегает?)
- Specificity level matches? (автор даёт цифры? примеры? или рассуждает?)
- Structural habits present? (как автор открывает? как заканчивает?)

Rewrite passages where voice has drifted, using corpus examples as reference register.

---

## Step 4 — Format-specific final check

**Telegram post**
- First line works as a standalone hook (читатель видит его в превью)?
- No paragraph longer than 3–4 lines?
- Ends with a point, not a summary?

**Carousel**
- Slide 1 hook: does it create tension or curiosity without resolving it?
- Each slide = one idea, max 2 sentences?
- Last slide: action or reframe — not "подписывайся" as the only payload?

**Reels script**
- Read it aloud. Awkward? Rewrite.
- No sentences longer than one breath?
- Opening 3 seconds: does it earn attention before explaining anything?

**Client report**
- Every claim has a number or a source?
- No sentence that could be deleted without losing information?
- Recommendations are specific (do X by Y date) not directional (consider improving X)?

---

## Step 5 — Final anti-AI audit

Ask: **"What still makes this obviously AI-generated?"**

List the remaining tells briefly, then rewrite to fix them.

This is the pass that catches what pattern-matching misses: sterile rhythm, generic examples, conclusions that say nothing, false balance ("on one hand… on the other hand…").

---

## Output format

Return:
1. The rewritten text
2. A brief edit log: what you changed and why (3–5 bullets max)
3. If voice drift was found: note which passages drifted and what you used from corpus to fix them

---

## What this skill does NOT do

- Does not fact-check claims — preserve all facts exactly as given
- Does not change the author's conclusions or opinions
- Does not add information that wasn't in the original
- Does not enforce one "correct" style — it enforces the author's style as defined by corpus
