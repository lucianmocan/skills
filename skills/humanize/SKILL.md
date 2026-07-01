---
name: humanize
description: Rewrite or review text to remove AI writing patterns and make it sound natural and human. Use when text sounds robotic, when you want to eliminate AI tells, when editing AI-generated drafts, or when writing should match a specific human voice.
---

# Humanize Writing

Audit and rewrite text to eliminate statistical and stylistic markers of AI generation, replacing them with patterns that match how humans actually write.

This skill works as instructions for any LLM tool (Claude Code, OpenCode, Codex, Hermes, etc.) or as a system prompt / inline instruction when writing from scratch.

## Usage

Provide a block of text to rewrite, or ask for an audit. When **rewriting**, apply the full protocol below. When **auditing**, flag each issue with a line-level note and offer a revised version.

**Core constraint:** Remove AI patterns, never content. When cutting a scaffolding sentence (warm-up, summary, scoping), the information it carried — if any — must be folded into the surrounding prose, not dropped. If a paragraph feels thin after edits, that is a signal content was lost, not that the paragraph was already short.

---

## The Seven AI Writing Tells

### 1. Subject-heavy sentence openers
AI opens >85% of sentences with a noun or pronoun subject. Humans open with 61%.

**Fix:** Front-load with adverbs, prepositional phrases, dependent clauses, or infinitives.
- ❌ `The study examines three key factors.`
- ✓ `To understand the gap, the study examines three factors.`
- ✓ `Across all three conditions, the same pattern held.`

### 2. Missing dependent clauses
AI uses dependent clauses in only 8% of sentences; humans use them in 39%.

**Fix:** Subordinate minor ideas instead of stacking independent clauses.
- ❌ `The model was retrained. It performed better.`
- ✓ `After retraining, the model performed better.`
- ✓ `Because the dataset shifted, the model needed retraining.`

### 3. Participial phrase sentence endings
AI ends sentences with dangling -ing phrases far more than humans do (28% vs. baseline).

**Fix:** Move modifiers to the front, restructure as a clause, or cut them.
- ❌ `The team proposed a new method, aiming to reduce latency.`
- ✓ `The team proposed a new method. The goal: cut latency.`
- ✓ `To reduce latency, the team proposed a new method.`

### 4. Banned words and phrases
Immediately replace any of the following:

| Category | Words to cut |
|---|---|
| Filler transitions | moreover, furthermore, additionally, consequently, thus |
| Inflated verbs | delve, leverage, utilize, facilitate, streamline, foster, harness, ensure, prioritize, aim |
| Dramatic nouns | tapestry, landscape, realm, journey, beacon, cornerstone, ecosystem (metaphorical) |
| Hedging openers | "It's worth noting that," "One might argue," "In the realm of" |
| Cliché openers | "In today's digital landscape," "In an era of," "At its core" |
| Overused AI verbs | aims, details, ensures, includes, involves, outlines, prioritizes |
| -ability/-ibility bloat | accessibility, portability, adjustability, retractability (when a simpler word works) |

**Replace with plain alternatives:**
- `utilize` → `use`
- `facilitate` → `help`, `let`, `make possible`
- `delve into` → `look at`, `dig into`
- `leverage` → `use`, `draw on`
- `ensure` → `make sure`, `guarantee`, or restructure

### 5. Sentence length uniformity (low burstiness)
AI sentences cluster around 20–25 words. 67% of AI sentences exceed 19 words.

**Fix:** Create contrast. Short sentences punch. Long ones carry the context, connect the ideas, and give the reader room to follow the logic before you land.
- Aim for a mix: some under 10 words, some over 25.
- Read the paragraph aloud — if it sounds metronomic, break it up.

### 6. Missing first person and contractions
AI avoids "we," "our," "I," and contractions even when the context calls for them.

**Fix:** Use first person when it's the natural voice. Use contractions in conversational or moderate-register writing.
- ❌ `It is recommended that one consider the tradeoffs.`
- ✓ `You'll want to weigh the tradeoffs here.`
- ❌ `The authors believe the results demonstrate...`
- ✓ `We think the results show...`

### 7. Inaccurate synonym substitution
AI replaces precise technical terms with approximate synonyms, introducing errors.

**Fix:** Never substitute a technical term. If the correct term is domain-specific, keep it and define it once if needed — don't replace it with something "simpler" that changes the meaning.

---

## Structural AI Patterns to Cut

These are paragraph-level constructions AI inserts automatically. They are harder to catch than individual words.

### Warm-up intro phrases
AI rarely opens with the claim. It introduces the introduction first.
- ❌ `A useful starting point is the idea of X.`
- ❌ `It is worth considering X.`
- ❌ `One key concept here is X.`
- ✓ Just state X directly.

### Paragraph-closing summary sentences
AI ends paragraphs by restating what the paragraph just showed. If the examples already demonstrate the point, the summary is redundant — cut it.
- ❌ `The details differ, but the goal is similar: [restatement of what was just described].`
- ❌ `In each case, the underlying principle is the same.`
- ✓ End on the last concrete fact. Let the reader draw the thread.

### Scoping / narrowing sentences
AI adds these at section ends to "transition" to a narrower focus.
- ❌ `These mechanisms are relevant to the broader X landscape, but this project focuses on Y.`
- ❌ `While all of these approaches matter, the focus here is Z.`
- ✓ Either cut entirely and open the next section with the narrower topic, or state the scope in one blunt sentence: `This project focuses on ARM TrustZone.`

### Generic transition openers
- ❌ `Other X make different tradeoffs.` (says nothing about what the tradeoffs are)
- ✓ Name the mechanism and immediately say what makes it different.

### Enumeration pattern across paragraphs
AI structures multi-point sections as prose lists: "One X… Another X… A third X…" as consecutive paragraph openers.
- ❌ `One obvious example is memory safety.` / `Another approach is formal verification.` / `A third approach is sandboxing.`
- ✓ Let the topic lead each paragraph: `Memory safety is the obvious place to start.` / `Formal verification takes a different route entirely.` / `Sandboxing takes a narrower goal: not correctness, but containment.`

### Warm-up section openers
AI prefaces a section by announcing what it is about to discuss.
- ❌ `Before discussing X, it is useful to look at Y.`
- ❌ `To understand X, we first need to consider Y.`
- ✓ Cut the announcement and open on the content directly. The section heading already signals the topic.

---

## Voice and Rhythm Fixes

**Add rhetorical questions** to create conversational flow and signal a thinking human:
- `Why does this matter? Because...`
- `Is this always the case? Not quite.`

**Add opinions and stance** where appropriate. AI hedges; humans assert.
- ❌ `Some may argue that this approach has merit.`
- ✓ `This approach works — at least when the data is clean.`

**Use specific details over generalities.** Humans recall concrete examples; AI generates abstractions.
- ❌ `There are many benefits to this method.`
- ✓ `In our last run, it cut processing time by 40%.`

**Break the symmetry.** AI paragraphs often have the same structure repeated. Vary paragraph length, vary the lead sentence type, occasionally start a paragraph with a question or a fragment.

---

## Rewriting Protocol

1. **Scan** for banned words (see table above) — replace all.
2. **Check openers** — if 3+ consecutive sentences start with a subject noun/pronoun, restructure. Cut warm-up intro phrases ("A useful starting point is…", "It is worth noting that…").
3. **Check endings** — strip participial tails or move them front. Cut paragraph-closing summary sentences that restate what the paragraph just showed.
4. **Check transitions** — delete scoping sentences ("X is relevant, but this focuses on Y") and generic openers ("Other X make different tradeoffs") — replace with something concrete.
5. **Check length** — if all sentences are 18–25 words, break or combine some.
6. **Add contractions** where register allows.
7. **Read aloud** — flag anything that sounds like a press release.
8. **Verify technical terms** — confirm nothing was quietly swapped for an inaccurate synonym.
9. **Check for lost content** — compare against the original; if a passage is shorter, confirm the missing material was pure scaffolding and not actual information that got dropped.

---

## Prompting AI to Write Better Initially

When generating fresh text, include these instructions:

```
- Do not start sentences with "The [noun]" more than twice per paragraph.
- Use dependent clauses and subordinating conjunctions.
- Do not end sentences with participial phrases ending in -ing.
- Avoid: moreover, furthermore, delve, leverage, utilize, tapestry, ensure, prioritize.
- Use contractions where natural.
- Do not substitute synonyms for technical terms.
- Vary sentence length: mix short (under 10 words) with longer ones.
- Write at least one sentence in the first person if appropriate.
```

---

## Quick Reference

**Always cut:** moreover · furthermore · additionally · delve · leverage · utilize · facilitate · tapestry · realm · beacon · cornerstone · "It's worth noting" · "In today's landscape" · "At its core"

**Always check:** sentence openers · -ing endings · sentence length distribution · first person absence · technical term accuracy · paragraph-closing summaries · scoping sentences · warm-up intros

**Always add:** one short sentence per paragraph · one concrete detail · contractions where the register allows
