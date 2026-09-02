<div align="center">

# 🔍 AI News Filter

**A Claude Cowork plugin that delivers only the AI news that matters for your work.**

[![Install](https://img.shields.io/badge/Install-Claude_Cowork-7F77DD?style=for-the-badge)](https://claude.ai)
[![License](https://img.shields.io/badge/License-MIT-1D9E75?style=for-the-badge)](LICENSE)

Built by **[Your Name]** · [LinkedIn](https://linkedin.com/in/yourprofile) · [Portfolio](https://yoursite.com)

</div>

---

## The story behind this

I was spending way too much energy consuming AI news. Every morning, a wave of announcements, launches, hot takes, funding rounds. And the headlines are designed to make everything feel urgent.

But here's what I realized:

**Consuming news — not just AI news — only generates anxiety.** It's impossible to keep up with everything. And 99% of what comes out is irrelevant to your actual life and work, no matter how loud the headline is.

So I started thinking about what a healthier relationship with AI news would look like. I landed on three principles:

### 1. Consume only from trusted sources

Not everything deserves your attention. I narrowed it down to four categories of sources I actually trust:

- **Labs** (who builds the models): OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral
- **Apps** (who builds on the models): Cursor, Lovable, ElevenLabs, Replit, Perplexity
- **Funds** (who invests in both): Sequoia, a16z, Y Combinator
- **Key people** (who shapes the thinking): Andrej Karpathy, Sam Altman, Dario Amodei, Elena Verna, among others

If it's not coming from one of these, it's probably noise.

### 2. Filter ruthlessly

Even from trusted sources, 90% of what comes out isn't relevant to *my* work. A new image generation model doesn't matter if I'm building enterprise workflows. A funding round in biotech AI doesn't change my week.

The filter I needed wasn't topic-based ("AI news") — it was **context-based** ("AI news that connects with what I'm actually doing right now").

### 3. Test, don't just read

It doesn't matter how many people say something is incredible. I don't know if it's real until I test it with my own hands. So the output needs to tell me not just *what happened* but *what I can try today*.

---

## So I built this

I turned these three principles into a Claude Cowork plugin that runs the whole process automatically. Here's how it works:

<div align="center">

<img src="docs/how-it-works.svg" alt="AI News Filter flow: context → search → filter → deliver" width="680">

</div>

**Step 1 — It reads your real context.** The plugin pulls from your calendar (next 7 days), your notes (last 7-14 days), and Claude's memory of your recent conversations. This builds a relevance profile: what are you working on, what tools are you using, what's on your mind this week.

**Step 2 — It searches only trusted sources.** 8-15 targeted web searches across Labs, Apps, Funds, and Key People. Primary sources only — official blogs, direct posts, published papers. No aggregators, no SEO content.

**Step 3 — It filters by relevance.** Every news item gets crossed against your context. Does it impact a project you're working on? Does it involve a tool you already use? Can you test it today? If not, it gets cut.

**Step 4 — It delivers 3-7 actionable items.** Each one explains *why it matters for you specifically*, not just what happened. Testable items include the path: which tool, which action, which link.

The result: instead of 45 minutes scrolling through noise, you spend 5 minutes reading what actually connects with your work.

---

## What you get

<table>
<tr>
<td width="50%">

### ❌ Without the filter

- 30+ articles across random sources
- Most are irrelevant to your work
- No way to know what to test
- 45 min scrolling, nothing actionable
- Anxiety from feeling behind

</td>
<td width="50%">

### ✅ With the filter

- 3-7 items from trusted sources only
- Each one explains why it matters **for you**
- Testable items include how-to steps
- 5 min reading, clear next actions
- Calm from knowing you saw what matters

</td>
</tr>
</table>

---

## Quick start

### 1. Download

Download [`ai-news-filter.plugin`](ai-news-filter.plugin) from this repo.

### 2. Install

Open Claude Desktop → Cowork → drag the `.plugin` file or use the install menu.

### 3. Connect your tools (optional)

The plugin works with just Claude's memory. But connecting these makes the filter sharper:

| Tool | What it adds |
|---|---|
| 📅 **Calendar** (Google Calendar, Outlook) | Reads your next 7 days to infer focus areas |
| 📝 **Notes** (Notion, Obsidian) | Reads recent pages to identify active projects |

### 4. Run it

```
AI news
/news
What happened in AI this week?
```

Or schedule it as a **weekly Cowork task** (I run mine every Friday morning).

---

## Customize it

Just tell Claude what you want. Changes persist across conversations.

| Say this | What happens |
|---|---|
| "Add Hugging Face to my sources" | New source tracked |
| "I don't care about image generation" | Topic blocked |
| "Make the filter broader" | More items per digest |
| "Also monitor AI regulation" | New topic added |
| "Remove Midjourney" | Source removed |

---

## Why I made the technical decisions I made

**Tool-agnostic connectors (`~~calendar`, `~~notes`)** — The plugin doesn't hardcode Google Calendar or Notion. It uses placeholder references so anyone can connect whatever calendar or notes app they use. This makes it portable.

**Sources in a separate reference file** — The trusted sources list lives in `references/trusted-sources.md`, not in the main skill. This means you can edit your sources without touching the core logic, and it keeps the main instruction file lean.

**Three layers of context** — Memory alone gives you the big picture but misses what's hot this week. Calendar alone shows meetings but not projects. Notes alone shows documents but not conversations. The three together build a context that's both deep and current.

**3-7 items, never more than 10** — This is a deliberate constraint. More than 10 and you're back to scrolling. The filter needs to be aggressive enough that what survives is genuinely worth your time.

---

## Inspiration

This plugin is inspired by [Deborah Folloni's method](https://www.linkedin.com/in/deborahfolloni/) for consuming less AI news while staying informed about what actually matters.

Her insight — that you don't need to know everything, just what connects with your work — is what drove the entire design.

---

<div align="center">

MIT License

</div>
