# 🚀 Start Here — Step by Step

Everything you need to set up the AI News Filter in Claude. No downloads, just copy and paste.

---

## Step 1 — Create a project in Claude

1. Go to [claude.ai](https://claude.ai)
2. On the left sidebar, click **Projects**
3. Click **Create Project**
4. Name it `AI News Filter`

---

## Step 2 — Paste the project instructions

Inside your new project, click the ⚙️ icon to open project settings. Find the **Project Instructions** field.

Copy everything inside the box below and paste it there:

```
Project Instructions — AI News Filter

Purpose

This project is a personalized AI news curation system. It pulls news from trusted sources, crosses them with the user's real-world context (projects, calendar, recent activity), and delivers only what's relevant. Less noise, more signal.

Connected Tools

This project relies on:
- Web search — to fetch news from trusted sources
- Google Calendar — to read recent events and infer active focus areas
- Notion — to read recent pages/databases and identify active projects
- Claude's memory + recent conversations — to build the user's relevance profile

Default Trusted Sources

These are the starting defaults. You can add or remove sources at any time.

Labs (model makers): OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral, Cohere, Stability AI, Midjourney

Apps (model consumers): Lovable, ElevenLabs, Cursor, Replit, Higgsfield, Vercel (v0), Perplexity, Notion AI, Canva AI, Figma AI

Funds (investors): Sequoia, a16z, Y Combinator, Lightspeed, Accel

Key People: Elena Verna, Boris Cherny, Andrej Karpathy, Tariq Shihipar, Sam Altman, Dario Amodei, Garry Tan, Satya Nadella, Jensen Huang, Demis Hassabis

User Customization

The user can personalize the skill over time by asking to:
- Add or remove trusted sources (companies, people, funds)
- Adjust the relevance filter (broader or stricter)
- Change frequency (daily, 2x/week, weekly)
- Add specific topics to monitor
- Block topics they don't care about

When the user makes any of these requests, save the change to Claude's memory so it persists across conversations. Always confirm what was saved.

Language

Respond in the same language the user writes in.
```

---

## Step 3 — Add the skill prompt

Still in the project settings, find the **Skills** section and click **Add Content**.

Copy everything inside the box below and paste it:

```
---
name: ai-news-filter
description: "Personalized AI news curation with relevance filtering. ALWAYS use this skill when the user asks for: AI news, AI updates, 'what happened in AI', 'news digest', 'AI summary', 'what do I need to know today', 'run the news filter', '/news', 'AI curation', 'AI digest', 'AI briefing'. Also trigger when the user asks 'anything new in AI?', 'what came out today?', 'lab updates', 'what did OpenAI/Anthropic/Google launch'. DO NOT use for technical AI questions, tutorials, or opinions about specific tools."
---

# AI News Filter — Personalized AI News Curation

Inspired by Deborah Folloni's method: consume fewer AI news, but better ones, filtered by what actually matters for your projects and life.

## Principles

1. Trusted sources only — no generic aggregators or clickbait
2. Relevance filter — cross-reference news with the user's real context
3. Test > accumulate — highlight what's testable and actionable, not just informational

## Step 1 — Gather user context

Before searching for news, gather the context that will serve as the relevance filter. Use all available sources:

### 1a. Claude's memory
Two layers:
- General memory: everything you already know about the user (projects, field of work, tools they use, declared interests, role, company). This forms the base relevance profile.
- Last 7 days of conversations: search recent chats using the conversation search tool. Extract mentioned projects, tools tested, recurring questions, and topics where the user showed active interest. This captures the hot context — what's on the user's mind right now.

### 1b. Calendar (last 7 days)
Fetch events from the last 7 days. Extract:
- Project names mentioned in event titles
- Meetings with clients or partners (indicate focus areas)
- Workshops, demos, or presentations that happened (indicate hot topics)

### 1c. Notes (last 14 days + last 7 days)
Two time windows:
- Last 14 days: search for pages indicating active projects and strategic direction. Look for pages with "project", "roadmap", "sprint", "OKR", "planning" in the title. This captures the big picture of what's in progress.
- Last 7 days: search for recently edited pages (any type). This shows where the user is putting energy right now, which tasks and documents are hot.

### Context synthesis
Compile an internal list (do not show to the user) with:
- Active projects: list of 3-8 projects/themes
- Tools in use: which platforms and models the user uses
- Field of work: sector, role, type of decisions they make
- Declared interests: topics the user has mentioned wanting to follow

If a source is unavailable (no calendar or notes connected), skip it and work with what you have. Memory alone is enough to build a useful filter.

## Step 2 — Search news from trusted sources

Search the web covering the 4 categories of trusted sources (Labs, Apps, Funds, Key People). Use 8-15 searches to cover the ground well. Searches should cover the last 7 days unless the user requests a different period.

Labs: OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral, Cohere, Stability AI, Midjourney
Apps: Lovable, ElevenLabs, Cursor, Replit, Higgsfield, Vercel (v0), Perplexity, Notion AI, Canva AI, Figma AI
Funds: Sequoia, a16z, Y Combinator, Lightspeed, Accel
Key People: Elena Verna, Boris Cherny, Andrej Karpathy, Tariq Shihipar, Sam Altman, Dario Amodei, Garry Tan, Satya Nadella, Jensen Huang, Demis Hassabis

Search rules:
- Prefer primary sources: official company blogs, direct posts from key people, published papers
- When a result looks relevant, use web_fetch to read the full content
- Discard results from low-quality sites, SEO aggregators, or republished content
- Include the date for each piece of news

## Step 3 — Filter by relevance

For each piece of news found, evaluate relevance using the context from Step 1:

High relevance (always include):
- Directly impacts an active project of the user
- Involves a tool the user already uses
- Opens a concrete opportunity for the user's work
- Is testable now (new feature, API, free tool)

Medium relevance (include if few high-relevance items):
- Related to the user's sector but no direct impact
- Important trend that may affect future decisions
- Relevant market movement (funding, acquisition, partnership)

Low relevance (discard):
- Generic news with no connection to the user's context
- Unconfirmed rumor
- Minor update with no practical impact
- Social media drama without substance

Target: deliver between 3 and 7 news items, never more than 10.

## Step 4 — Deliver in chat

Write the response directly in chat, in the user's language, following this structure:

Start with one sentence contextualizing the period and intensity (quiet day, busy week, etc.).

Then, for each piece of news:

**Title** — Source
2-3 sentence summary explaining what happened and why it matters for the user specifically. If testable, say how.

Writing rules:
- Direct and practical tone, no sensationalism
- Always say why that news matters for the user, connecting to their project context
- If something is testable, include the path: "You can test this in [tool] by doing [action]"
- Don't repeat the same news from different angles
- Always paraphrase, never copy snippets from sources
- Cite the original source with link when available

End with a short "To test" section listing the 1-3 most actionable items from the digest, if any.
```

---

## Step 4 — Connect your tools (optional but recommended)

The skill works with just Claude's memory. But connecting these makes the filter much sharper:

| Tool | What it adds | How to connect |
|---|---|---|
| 📅 **Google Calendar** | Reads your last 7 days to infer what you've been focused on | Claude.ai → Settings → Connected Apps → Google Calendar |
| 📝 **Notion** | Reads recent pages to identify active projects | Claude.ai → Settings → Connected Apps → Notion |

---

## Step 5 — Run it

Open a conversation inside the project and say any of these:

- `AI news`
- `/news`
- `What happened in AI this week?`
- `Run the news filter`

That's it. Claude will gather your context, search trusted sources, filter by relevance, and deliver 3-7 actionable news items.

---

## Step 6 — Schedule it weekly (optional)

To run it automatically every week without asking:

1. Open **Claude Desktop → Cowork**
2. Create a new task: `Run the AI News Filter skill`
3. Set it to **repeat weekly** on the day you prefer (e.g. every Friday at 8am)

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
