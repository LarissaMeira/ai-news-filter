<div align="center">

# 🔍 AI News Filter (Claude)

**Stop drowning in AI news. Get only what matters for your work.**

A system built inside Claude that pulls from trusted sources, crosses them with your real-world context, and delivers only what's relevant.

</div>

---

## The story behind this

I was spending way too much energy consuming AI news. Every morning, a wave of announcements, launches, hot takes, funding rounds. And the headlines are designed to make everything feel urgent.

But here's what I realized:

**Consuming news — not just AI news — only generates anxiety.** It's impossible to keep up with everything. And 99% of what comes out is irrelevant to your actual life and work, no matter how loud the headline is.

So I started thinking about what a healthier relationship with AI news would look like. I landed on three principles:

### 1. Consume only from trusted sources

Not everything deserves your attention. I narrowed it down to four categories of sources I actually trust:

- **Labs** (who builds the models): OpenAI, Anthropic, Google, DeepMind, Meta AI, Mistral, Microsoft
- **Apps** (who builds on the models): Cursor, Lovable, ElevenLabs, Replit, Perplexity
- **Funds** (who invests in both): Sequoia, a16z, Y Combinator
- **Key people** (who shapes the thinking): Andrej Karpathy, Sam Altman, Dario Amodei, Elena Verna, among others

These are the sources I tend to prioritize.

### 2. Filter ruthlessly

Even from trusted sources, 90% of what comes out isn't relevant to *my* work. A new image generation model doesn't matter if I'm building enterprise workflows. A funding round in biotech AI doesn't change my week.

The filter I needed wasn't topic-based ("AI news") — it was **context-based** ("AI news that connects with what I'm actually doing right now").

### 3. Test, don't just read

It doesn't matter how many people say something is incredible. I don't know if it's real until I test it with my own hands. So the output needs to tell me not just *what happened* but *what I can try today*.

---

## So I built this

I turned these three principles into a system that runs inside Claude. Here's how it works:

**Step 1 — It reads your real context.** It pulls from your calendar (last 7 days), your notes (last 7-14 days), and Claude's memory of your recent conversations and also the files inside the project. This builds a relevance profile: what are you working on, what tools are you using, what's on your mind this week.

**Step 2 — It searches only trusted sources.** 8-15 targeted web searches across Labs, Apps, Funds, and Key People. Primary sources only — official blogs, direct posts, published papers. No aggregators, no SEO content.

**Step 3 — It filters by relevance.** Every news item gets crossed against your context. Does it impact a project you're working on? Does it involve a tool you already use? Can you test it today? If not, it gets cut.

**Step 4 — It delivers a PDF report.** News first, grouped by relevance, with real substance per item (not headline blurbs). Then a "What to apply" section connecting each relevant item to your own tools and projects. Testable items include the path: which tool, which action, which link.

The result: instead of 45 minutes scrolling through noise, you spend 5 minutes reading what actually connects with your work.

---

## How to set it up (3 minutes)

Everything below is copy and paste. No files to download, no packages to install.

### Step 1 — Create a project in Claude

1. Go to [claude.ai](https://claude.ai)
2. On the left sidebar, click **Projects**
3. Click **Create Project**
4. Name it `AI News Filter`

### Step 2 — Paste the project instructions

Inside your new project, click the ⚙️ icon to open project settings. Find the **Project Instructions** field.

Copy everything inside the box below and paste it there:

```
Project Instructions — AI News Filter

This project uses the skill /ai-news-filter. When the user asks for AI news, updates, digest, or says /news, always activate this skill and follow its full instructions.

Purpose

This project is a personalized AI news curation system. It pulls news from trusted sources, crosses them with the user's real-world context (projects, calendar, recent activity), and delivers only what's relevant. Less noise, more signal.

Connected Tools

This project relies on:
- Web search — to fetch news from trusted sources
- Google Calendar — to read recent events and infer active focus areas
- Notion — to read recent pages/databases and identify active projects
- Gmail — to read recent email threads (skipping newsletters and automated mail) and infer active client and project context
- Claude's memory + recent conversations — to build the user's relevance profile

Default Trusted Sources

Labs (model makers): OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral, Cohere, Stability AI, Midjourney

Apps (model consumers): Lovable, ElevenLabs, Cursor, Replit, Higgsfield, Vercel (v0), Perplexity, Notion AI, Canva AI, Figma AI

Funds (investors): Sequoia, a16z, Y Combinator, Lightspeed, Accel

Key People: Elena Verna, Boris Cherny, Andrej Karpathy, Tariq Shihipar, Sam Altman, Dario Amodei, Garry Tan, Satya Nadella, Jensen Huang, Demis Hassabis

User Customization

The user can personalize the skill over time by asking to:
- Add or remove trusted sources
- Adjust the relevance filter
- Change frequency
- Add specific topics to monitor
- Block topics they don't care about

Language: Respond in the same language the user writes in.

Default Search Period: last 7 days. The user can override this in the prompt, and the user can also run it via a Cowork scheduled task.

Default targets by period:
- Last 3 days: 4-8 items
- Last 7 days: 8-15 items
```

### Step 3 — Add the skill

Download the skill file [`ai-news-filter-skill.md`](ai-news-filter-skill.md) from this repo (click the file, then click the **Download raw file** button ↓).

After download, still in the project, go to **Skills → Manage Skills → Add → Upload Skill**.

### Step 4 — Connect your tools (recommended)

The skill works with just Claude's memory. But connecting these makes the filter sharper:

| Tool | What it adds | How to connect |
|---|---|---|
| 📅 **Google Calendar** | Reads your last 7 days to infer focus areas | [Claude.ai](http://Claude.ai) → Settings → Connected Apps → Google Calendar |
| 📝 **Notion** | Reads recent pages to identify active projects | [Claude.ai](http://Claude.ai) → Settings → Connected Apps → Notion |
| 🎤 **Granola AI** | Reads meeting transcripts to capture topics, decisions, and active client conversations | [Claude.ai](http://Claude.ai) → Settings → Connected Apps → Granola |
| 📧 **Gmail** | Reads recent email threads (skipping newsletters and automated mail) to capture client names and active project context | [Claude.ai](http://Claude.ai) → Settings → Connected Apps → Gmail |

### Step 5 — Run it

Open a conversation inside the project and say any of these:

- `AI news`
- `/news`
- `What happened in AI this week?`

That's it. Claude will gather your context, search trusted sources, filter by relevance, and deliver 8-15 actionable news items.

### Step 6 — Schedule it automatically (optional)

You can set Claude to run this on autopilot, so your digest is ready when you open the project.

1. Open your **AI News Filter** project in [claude.ai](https://claude.ai)
2. In the project settings (left panel), scroll down to the **Scheduled** section
3. Click the **+** button
4. In **Name**, type: `AI News - Weekly Briefing`
5. In **Prompt**, paste this:

```
Run the AI News Filter skill. Do not repeat news from previous runs.
```

6. In **Cadence**, choose the frequency that works for you (weekly, every 3 days, twice a week, etc.)
7. Done. Claude will run the skill at the scheduled time and leave the digest in a new conversation inside the project.

**Tip:** You can adjust the period in the prompt. For example, change "last 7 days" to "last 3 days" if you want to run it more frequently with a shorter window.

You can edit or remove the schedule anytime from the same section.

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
| "8-12 items, never more than 15" | New constraint |

---

## Why I made these technical decisions

**Three layers of context** — Memory alone gives you the big picture but misses what's hot this week. Calendar alone shows meetings but not projects. Notes alone shows documents but not conversations. The three together build a context that's both deep and current.

**8-15 items** — This is a deliberate constraint. More than 10 and you're back to scrolling. The filter needs to be aggressive enough that what survives is genuinely worth your time.

**Sources separated from logic** — The trusted sources are listed explicitly so you can edit them without touching the core prompt. Add a company, remove a person, block a topic — all without breaking anything.
