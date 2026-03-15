---
name: humanizer-ru-voice
version: 2.0.0
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
Based on [blader/humanizer v2.2.0](https://github.com/blader/humanizer) with additions for:
- Russian-language AI patterns
- Format-specific rules (Telegram, carousels, Reels, client reports)
- Voice corpus calibration
- Personality and soul injection

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

## Step 2 — Personality and soul

Avoiding AI patterns is only half the job. Sterile, voiceless writing is just as obvious as slop. Good writing has a human behind it.

### Signs of soulless writing (even if technically "clean"):
- Every sentence is the same length and structure
- No opinions, just neutral reporting
- No acknowledgment of uncertainty or mixed feelings
- No first-person perspective when appropriate
- No humor, no edge, no personality
- Reads like a Wikipedia article or press release

### How to add voice:

**Have opinions.** Don't just report facts — react to them. "Я сам не до конца понимаю, как к этому относиться" is more human than neutrally listing pros and cons.

**Vary your rhythm.** Short punchy sentences. Then longer ones that take their time getting where they're going. Mix it up.

**Acknowledge complexity.** Real humans have mixed feelings. "Это впечатляет, но немного пугает" beats "Это впечатляет."

**Use "I" when it fits.** First person isn't unprofessional — it's honest. "Я всё время возвращаюсь к мысли..." signals a real person thinking.

**Let some mess in.** Perfect structure feels algorithmic. Tangents, asides, and half-formed thoughts are human.

**Be specific about feelings.** Not "это вызывает опасения" but "есть что-то тревожное в том, как агенты молотят код в три ночи, пока все спят."

> **Note:** If corpus is loaded, these are secondary to the author's actual voice. Soul comes from the corpus first, these principles second.

---

## Step 3 — Universal AI pattern check

Scan for all of the following and rewrite affected passages.

> **Note:** The examples below illustrate the *direction* of the fix, not the target style.
> Target style is defined solely by CORPUS.md. If a corpus is loaded, adapt all rewrites
> to match its rhythm and tone — not the phrasing of these examples.

---

### RU patterns (Russian-specific AI tells)

#### RU-1. Канцелярит и вводные конструкции

Words to watch: важно отметить, стоит подчеркнуть, необходимо учитывать, следует отметить, хотелось бы обратить внимание, в данном контексте, данный/данная/данное (вместо «этот»), осуществляет, является, в рамках, в целях, посредством
Fix: Cut entirely or replace with direct statement.

> ❌ Важно отметить, что данный подход осуществляет переход к новой модели.
> ✅ Подход меняет модель.

#### RU-2. AI-превосходные степени

Words to watch: уникальный, революционный, передовой, инновационный, ключевой, значимый, актуальный, эффективный (без доказательств)
Fix: Delete or replace with a specific fact.

> ❌ Это уникальное и инновационное решение для современного бизнеса.
> ✅ Решение сокращает время онбординга с 3 недель до 4 дней.

#### RU-3. Обобщающие финалы

Phrases to watch: таким образом, подводя итог, в заключение, в конечном счёте, в современном мире, в эпоху цифровизации
Fix: End with a concrete statement or a question, not a summary bow.

#### RU-4. "Мы живём в мире, где..."

Problem: AI любит открывать текст с глобального контекста.
Fix: Start with конкретным фактом или наблюдением.

> ❌ В современном мире маркетинг переживает трансформацию.
> ✅ ChatGPT отвечает на 10 миллиардов запросов в месяц. Часть из них — про твой бренд.

#### RU-5. Троица прилагательных

Problem: AI стекирует по три синонима для усиления.
Words to watch: быстрый, удобный и надёжный / точный, структурированный и понятный
Fix: Оставь одно — самое точное.

---

### EN patterns (English AI tells)

#### EN-1. Undue emphasis on significance, legacy, and broader trends

**Words to watch:** stands/serves as, is a testament/reminder, a vital/significant/crucial/pivotal/key role/moment, underscores/highlights its importance/significance, reflects broader, symbolizing its ongoing/enduring/lasting, contributing to the, setting the stage for, marking/shaping the, represents/marks a shift, key turning point, evolving landscape, focal point, indelible mark, deeply rooted

**Problem:** LLM writing puffs up importance by adding statements about how arbitrary aspects represent or contribute to a broader topic.

> ❌ The Statistical Institute of Catalonia was officially established in 1989, marking a pivotal moment in the evolution of regional statistics in Spain.
> ✅ The Statistical Institute of Catalonia was established in 1989 to collect and publish regional statistics independently from Spain's national statistics office.

#### EN-2. Undue emphasis on notability and media coverage

**Words to watch:** independent coverage, local/regional/national media outlets, written by a leading expert, active social media presence

**Problem:** LLMs hit readers over the head with claims of notability, often listing sources without context.

> ❌ Her views have been cited in The New York Times, BBC, Financial Times, and The Hindu. She maintains an active social media presence with over 500,000 followers.
> ✅ In a 2024 New York Times interview, she argued that AI regulation should focus on outcomes rather than methods.

#### EN-3. Superficial analyses with -ing endings

**Words to watch:** highlighting/underscoring/emphasizing..., ensuring..., reflecting/symbolizing..., contributing to..., cultivating/fostering..., encompassing..., showcasing...

**Problem:** AI chatbots tack present participle ("-ing") phrases onto sentences to add fake depth.

> ❌ The temple's color palette resonates with the region's natural beauty, symbolizing Texas bluebonnets, reflecting the community's deep connection to the land.
> ✅ The temple uses blue, green, and gold. The architect said these were chosen to reference local bluebonnets and the Gulf coast.

#### EN-4. Promotional and advertisement-like language

**Words to watch:** boasts a, vibrant, rich (figurative), profound, enhancing its, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking (figurative), renowned, breathtaking, must-visit, stunning

**Problem:** LLMs have problems keeping a neutral tone, especially for "cultural heritage" topics.

> ❌ Nestled within the breathtaking region of Gonder, Alamata stands as a vibrant town with a rich cultural heritage and stunning natural beauty.
> ✅ Alamata is a town in the Gonder region of Ethiopia, known for its weekly market and 18th-century church.

#### EN-5. Vague attributions and weasel words

**Words to watch:** Industry reports, Observers have cited, Experts argue, Some critics argue, several sources/publications (when few cited), Studies show, research suggests

**Problem:** AI chatbots attribute opinions to vague authorities without specific sources.

> ❌ Experts believe the river plays a crucial role in the regional ecosystem.
> ✅ The river supports several endemic fish species, according to a 2019 survey by the Chinese Academy of Sciences.

#### EN-6. Outline-like "Challenges and Future Prospects" sections

**Words to watch:** Despite its... faces several challenges..., Despite these challenges, Challenges and Legacy, Future Outlook

**Problem:** Many LLM-generated articles include formulaic "Challenges" sections that always resolve optimistically.

> ❌ Despite its industrial prosperity, Korattur faces challenges typical of urban areas. Despite these challenges, Korattur continues to thrive.
> ✅ Traffic congestion increased after 2015 when three new IT parks opened. The municipal corporation began a stormwater drainage project in 2022.

#### EN-7. Overused AI vocabulary (full list)

**High-frequency AI words:** Additionally, align with, crucial, delve, emphasizing, enduring, enhance, fostering, garner, highlight (verb), interplay, intricate/intricacies, key (adjective), landscape (abstract noun), multifaceted, nuanced (overused), pivotal, showcase, tapestry (abstract noun), testament, underscore (verb), valuable, vibrant, navigate, mosaic, holistic, synergy, paradigm shift, game-changer, unlock, supercharge, elevate, pivot, seamless, robust, leverage, innovative

**Problem:** These words appear far more frequently in post-2023 text. They often co-occur.

Fix: Replace with plain or specific language.

#### EN-8. Copula avoidance

**Words to watch:** serves as / stands as / marks / represents [a], boasts / features / offers [a]

**Problem:** LLMs substitute elaborate constructions for simple copulas (is/are/has).

> ❌ Gallery 825 serves as LAAA's exhibition space. The gallery features four spaces and boasts over 3,000 sq ft.
> ✅ Gallery 825 is LAAA's exhibition space. The gallery has four rooms totaling 3,000 sq ft.

#### EN-9. Negative parallelisms

**Problem:** "Not only...but..." or "It's not just about..., it's..." are overused for false profundity.

> ❌ It's not just about the beat; it's part of the aggression. It's not merely a song, it's a statement.
> ✅ The heavy beat adds to the aggressive tone.

Fix: Delete entirely or replace with a specific claim.

#### EN-10. Rule of three overuse

**Problem:** LLMs force ideas into groups of three to appear comprehensive.

> ❌ The event features keynote sessions, panel discussions, and networking opportunities.
> ✅ The event includes talks and panels. There's also time for informal networking.

Fix: If only two things matter, say two.

#### EN-11. Elegant variation (synonym cycling)

**Problem:** AI has repetition-penalty code causing excessive synonym substitution for the same referent.

> ❌ The protagonist faces challenges. The main character must overcome obstacles. The central figure triumphs. The hero returns home.
> ✅ The protagonist faces many challenges but eventually triumphs and returns home.

Fix: Pick one term and stick with it.

#### EN-12. False ranges

**Problem:** LLMs use "from X to Y" constructions where X and Y aren't on a meaningful scale.

> ❌ Our journey has taken us from the singularity of the Big Bang to the cosmic web, from the birth of stars to the dance of dark matter.
> ✅ The book covers the Big Bang, star formation, and current theories about dark matter.

#### EN-13. Em dash overuse

**Problem:** LLMs use em dashes more than humans, mimicking "punchy" sales writing.

Fix: Use period or restructure. One em dash per paragraph maximum.

> ❌ The term is promoted by Dutch institutions—not by the people themselves. You don't say "Netherlands, Europe"—yet this mislabeling continues—even in official documents.
> ✅ The term is promoted by Dutch institutions, not by the people themselves. You don't say "Netherlands, Europe" as an address, yet this mislabeling continues in official documents.

#### EN-14. Overuse of boldface

**Problem:** AI chatbots emphasize phrases in boldface mechanically.

> ❌ It blends **OKRs**, **KPIs**, and tools such as the **Business Model Canvas** and **Balanced Scorecard**.
> ✅ It blends OKRs, KPIs, and tools like the Business Model Canvas and Balanced Scorecard.

Fix: Remove bold unless it serves a genuine visual function (e.g., a definition list in docs).

#### EN-15. Inline-header vertical lists (bold header lists)

**Problem:** AI outputs lists where items start with bolded headers followed by colons.

> ❌ - **User Experience:** The UX has been significantly improved.
> - **Performance:** Performance has been enhanced through optimized algorithms.
> ✅ The update improves the interface and speeds up load times through optimized algorithms.

Fix: Convert to flowing sentences unless the format genuinely requires a list.

#### EN-16. Title Case in headings

**Problem:** AI chatbots capitalize all main words in headings (Title Case).

> ❌ ## Strategic Negotiations And Global Partnerships
> ✅ ## Strategic negotiations and global partnerships

Fix: Use sentence case unless house style requires Title Case.

#### EN-17. Emojis in structure

**Problem:** AI chatbots decorate headings or bullet points with emojis.

> ❌ Launch Phase: The product launches in Q3
> ✅ The product launches in Q3.

Fix: Remove emojis from structural elements. Emojis may be kept only if the author's voice (corpus) uses them intentionally.

#### EN-18. Curly quotation marks

**Problem:** ChatGPT uses curly quotes instead of straight quotes.

Fix: Replace curly quotes with straight quotes, unless house style specifies otherwise.

#### EN-19. Collaborative communication artifacts (chatbot residue)

**Words to watch:** I hope this helps, Of course!, Certainly!, You're absolutely right!, Would you like..., let me know, here is a..., Great question!

**Problem:** Text meant as chatbot correspondence gets pasted as content.

> ❌ Here is an overview of the French Revolution. I hope this helps! Let me know if you'd like me to expand on any section.
> ✅ The French Revolution began in 1789 when financial crisis and food shortages led to widespread unrest.

Fix: Delete all chatbot residue. Content should read as standalone text.

#### EN-20. Knowledge-cutoff disclaimers

**Words to watch:** as of [date], Up to my last training update, While specific details are limited/scarce..., based on available information...

**Problem:** AI disclaimers about incomplete information get left in text.

> ❌ While specific details about the company's founding are not extensively documented in readily available sources, it appears to have been established sometime in the 1990s.
> ✅ The company was founded in 1994, according to its registration documents.

Fix: Remove the disclaimer. Either state the fact with a source or omit it.

#### EN-21. Sycophantic / servile tone

**Problem:** Overly positive, people-pleasing language.

> ❌ Great question! You're absolutely right that this is a complex topic. That's an excellent point!
> ✅ The economic factors you mentioned are relevant here.

Fix: Remove flattery. Respond to the substance, not the person.

#### EN-22. Filler phrases

Common substitutions:
- "In order to achieve this goal" → "To achieve this"
- "Due to the fact that" → "Because"
- "At this point in time" → "Now"
- "In the event that" → "If"
- "The system has the ability to" → "The system can"
- "It is important to note that the data shows" → "The data shows"

Fix: Replace with shorter equivalent.

#### EN-23. Excessive hedging

**Problem:** Over-qualifying statements with stacked modals.

> ❌ It could potentially possibly be argued that the policy might have some effect on outcomes.
> ✅ The policy may affect outcomes.

Fix: One hedge word maximum per claim.

#### EN-24. Generic positive conclusions

**Problem:** Vague upbeat endings that say nothing.

> ❌ The future looks bright. Exciting times lie ahead as they continue their journey toward excellence.
> ✅ The company plans to open two more locations next year.

Fix: End with a specific fact or leave it out.

---

## Step 4 — Voice drift check (if corpus loaded)

After removing AI patterns, compare against the voice fingerprint from Step 0.

Ask: **"Does this sound like [author] or does it sound like a clean, voiceless version of [author]?"**

Flags to check:
- Sentence rhythm matches corpus? (длина, ритм чередования)
- Degree of first-person presence matches? (автор пишет "я" или избегает?)
- Specificity level matches? (автор даёт цифры? примеры? или рассуждает?)
- Structural habits present? (как автор открывает? как заканчивает?)

Rewrite passages where voice has drifted, using corpus examples as reference register.

---

## Step 5 — Format-specific final check

**Telegram post**
- First line works as a standalone hook (читатель видит его в превью)?
- No paragraph longer than 3-4 lines?
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

## Step 6 — Final anti-AI audit

Two-pass process:

**Pass 1:** Ask: **"What still makes this obviously AI-generated?"**
List the remaining tells briefly, then rewrite to fix them.

**Pass 2:** After rewriting, ask again: **"Now make it not obviously AI generated."**
Revise once more. This catches what pattern-matching misses: sterile rhythm, generic examples, conclusions that say nothing, false balance ("on one hand... on the other hand...").

---

## Output format

Return:
1. The rewritten text
2. A brief edit log: what you changed and why (3-5 bullets max)
3. If voice drift was found: note which passages drifted and what you used from corpus to fix them

---

## What this skill does NOT do

- Does not fact-check claims — preserve all facts exactly as given
- Does not change the author's conclusions or opinions
- Does not add information that wasn't in the original
- Does not enforce one "correct" style — it enforces the author's style as defined by corpus

---

## Reference

EN patterns based on [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), maintained by WikiProject AI Cleanup, via [blader/humanizer v2.2.0](https://github.com/blader/humanizer).
