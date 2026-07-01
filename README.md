# skills

Personal LLM skill library. Works with Claude Code, OpenCode, Codex, Hermes, and any tool that accepts markdown instruction files or inline prompts.

## Skills

### `humanize`

Rewrites or audits text to remove AI writing patterns and make it sound natural.

**When to use:** text sounds robotic, editing an AI-generated draft, writing from scratch and want to avoid AI tells, or matching a specific human voice.

**What it checks and fixes:**
- Subject-heavy sentence openers (AI: >85%, human: 61%)
- Missing dependent clauses (AI: 8%, human: 39%)
- Participial phrase sentence endings (AI: 28%)
- Banned words and phrases: *moreover, furthermore, delve, leverage, utilize, tapestry, cornerstone, ensure, prioritize*, hedging openers, cliché openers, and more
- Uniform sentence length (low burstiness — AI sentences cluster around 20–25 words)
- Missing first person and contractions
- Inaccurate synonym substitution for technical terms

**File:** [`skills/humanize/SKILL.md`](skills/humanize/SKILL.md)

---

## Sources

- [CraftSciCom — Signs of AI Writing](https://www.craftscicom.org/ai_signs.html) — quantitative grammar and style analysis: sentence opener ratios, dependent clause rates, participial endings, overused verbs, sentence length distributions
- [Surfer SEO — How to Avoid AI Detection](https://surferseo.com/blog/avoid-ai-detection/) — banned word lists, burstiness concept, structural and stylistic fixes, editorial review checklist
