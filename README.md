<div align="center">

# 🔍 AI News Filter

**Stop drowning in AI news. Get only what matters for your work.**

[![Claude](https://img.shields.io/badge/Built_for-Claude-7F77DD?style=for-the-badge)](https://claude.ai)
[![License](https://img.shields.io/badge/License-MIT-1D9E75?style=for-the-badge)](LICENSE)

Built by **[Your Name]** · [LinkedIn](https://linkedin.com/in/yourprofile)

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

I turned these three principles into a system that runs inside Claude. Here's how it works:

**Step 1 — It reads your real context.** It pulls from your calendar (last 7 days), your Notion (last 7-14 days), your Granola meeting transcripts (last 7 days), and Claude's memory of your recent conversations. This builds a relevance profile: what are you working on, what tools are you using, what's on your mind this week.

**Step 2 — It searches only trusted sources.** 8-15 targeted web searches across Labs, Apps, Funds, and Key People. Primary sources only — official blogs, direct posts, published papers. No aggregators, no SEO content.

**Step 3 — It filters by relevance.** Every news item gets crossed against your context. Does it impact a project you're working on? Does it involve a tool you already use? Can you test it today? If not, it gets cut.

**Step 4 — It delivers 8-15 actionable items.** Each one explains *why it matters for you specifically*, not just what happened. Testable items include the path: which tool, which action, which link.

The result: instead of 45 minutes scrolling through noise, you spend 5 minutes reading what actually connects with your work.

---

## What you get

<table>
<tr>
<td width="50%">

### ❌ Without the filter

- 100+ articles across random sources
- Most are irrelevant to your work
- No way to know what to test
- 45 min scrolling, nothing actionable
- Anxiety from feeling behind

</td>
<td width="50%">

### ✅ With the filter

- 8-15 items from trusted sources only
- Each one explains why it matters **for you**
- Testable items include how-to steps
- 5 min reading, clear next actions
- Calm from knowing you saw what matters

</td>
</tr>
</table>

---

## How to set it up (5 minutes)

### Step 1 — Create a project in Claude

1. Go to [claude.ai](https://claude.ai)
2. On the left sidebar, click **Projects**
3. Click **Create Project**
4. Name it `AI News Filter`

### Step 2 — Paste the project instructions

Inside your new project, click the ⚙️ icon to open project settings. Find the **Project Instructions** field.

Click the 📋 button in the top-right corner of the box below to copy, then paste it in.

```
Project Instructions — AI News Filter

Skill

This project uses the skill "ai-news-filter". When the user asks for AI news, updates, digest, or says /news, always activate this skill and follow its full instructions.

Purpose

Personalized AI news curation. Pull from trusted sources, cross with the user's real context, deliver only what's relevant. Less noise, more signal.

Connected Tools

This project relies on:
- Web search — fetch news from trusted sources
- Google Calendar — read last 7 days of events to infer focus areas
- Notion — read recent pages/databases to identify active projects
- Granola — read recent meeting transcripts for topics, decisions, and client context
- Claude's memory + recent conversations — build the user's relevance profile

Default Trusted Sources

Labs: OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral, Cohere, Stability AI, Midjourney
Apps: Lovable, ElevenLabs, Cursor, Replit, Higgsfield, Vercel (v0), Perplexity, Notion AI, Canva AI, Figma AI
Funds: Sequoia, a16z, Y Combinator, Lightspeed, Accel
Key People: Elena Verna, Boris Cherny, Andrej Karpathy, Tariq Shihipar, Sam Altman, Dario Amodei, Garry Tan, Satya Nadella, Jensen Huang, Demis Hassabis

Default Search Period: last 7 days. The user can override this in the prompt or via the Cowork scheduled task.

Default targets by period:
- Last 3 days: 4-8 items
- Last 7 days: 8-15 items

Do not repeat news already delivered in previous runs.

User Customization

The user can add/remove sources, adjust the filter, change frequency, add topics to monitor, or block topics. Save any change to Claude's memory and confirm what was saved.

Language

Respond in the same language the user writes in.
```

### Step 3 — Add the skill

Download the skill file [`ai-news-filter-skill.md`](ai-news-filter-skill.md) from this repo (click the file, then click the **Download raw file** button ↓).

Then in Claude:
1. Inside your project, click the **+** icon
2. Go to **Skills → Manage Skills → Add → Upload Skill**
3. Upload the `ai-news-filter-skill.md` file
4. Done — the skill is now active

### Step 4 — Connect your tools (optional but recommended)

The skill works with just Claude's memory. But connecting these makes the filter sharper:

| Tool | What it adds | How to connect |
|---|---|---|
| 📅 **Google Calendar** | Reads your last 7 days to infer focus areas | Claude.ai → Settings → Connected Apps → Google Calendar |
| 📝 **Notion** | Reads recent pages to identify active projects | Claude.ai → Settings → Connected Apps → Notion |
| 🎤 **Granola AI** | Reads meeting transcripts for topics, decisions, and client context | Claude.ai → Settings → Connected Apps → Granola |

### Step 5 — Run it

Open a conversation inside the project and say any of these:

- `AI news`
- `/news`
- `What happened in AI this week?`
- `Run the news filter`

That's it. Claude will gather your context, search trusted sources, filter by relevance, and deliver 8-15 actionable news items.

### Step 6 — Schedule it automatically (optional)

1. Open your **AI News Filter** project in [claude.ai](https://claude.ai)
2. In the project settings, scroll down to the **Scheduled** section
3. Click **+**
4. **Name**: `AI News - Weekly Briefing`
5. **Prompt**: `Run the AI News Filter skill. Do not repeat news from previous runs.`
6. **Cadence**: choose what works for you (weekly, every 3 days, etc.)

---

## Customize it anytime

Just tell Claude what you want inside the project. Changes persist across conversations.

| Say this | What happens |
|---|---|
| "Add Hugging Face to my sources" | New source tracked |
| "I don't care about image generation" | Topic blocked |
| "Make the filter broader" | More items per digest |
| "Also monitor AI regulation" | New topic added |
| "Remove Midjourney" | Source removed |

---

## Why I made these technical decisions

**Four layers of context** — Memory gives the big picture. Calendar shows what you've been doing. Notion shows active projects. Granola captures what was discussed in meetings. Together they build a context that's both deep and current.

**8-15 items, scaled by period** — The target adjusts to how much time you're covering. 3 days gets 4-8 items, 7 days gets 8-15. Never pads with low-relevance items just to hit the number.

**Sources separated from logic** — The trusted sources are listed in the project instructions so you can edit them without touching the skill. Add a company, remove a person, block a topic — all without breaking anything.

**Period defined in project instructions, not in the skill** — The skill doesn't hardcode a time window. The project instructions set the default, and the user or Cowork schedule can override it. Each layer has its own job.

---

## Inspiration

This project is inspired by [Deborah Folloni's method](https://www.linkedin.com/in/deborahfolloni/) for consuming less AI news while staying informed about what actually matters.

Her insight — that you don't need to know everything, just what connects with your work — is what drove the entire design.

---

<div align="center">

MIT License

</div>
