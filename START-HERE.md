# 🚀 Start Here — Step by Step

Everything you need to set up the AI News Filter in Claude, from zero to running.

---

## Step 1 — Download two files from this repo

You need two files. Click each one in the file list above, then click the **Download** button (↓).

| File | What it is |
|---|---|
| `ai-news-filter.plugin` | The plugin itself (the skill that does the work) |
| `START-HERE.md` | This guide (you're reading it — also contains the project instructions to paste in Step 3) |

---

## Step 2 — Create a project in Claude

1. Go to [claude.ai](https://claude.ai)
2. On the left sidebar, click **Projects**
3. Click **Create Project**
4. Name it `AI News Filter` (or whatever you prefer)

---

## Step 3 — Paste the project instructions

Inside your new project, open **Settings** and find the **Project Instructions** field.

Copy everything below the line and paste it there:

---

### ✂️ Copy from here ↓

```
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

You can personalize the skill over time by asking to:
- Add or remove trusted sources (companies, people, funds)
- Adjust the relevance filter (broader or stricter)
- Change frequency (daily, 2x/week, weekly)
- Add specific topics to monitor
- Block topics you don't care about

When you make any of these requests, Claude saves the change to memory so it persists across conversations.

Language

Respond in the same language the user writes in.
```

### ✂️ Stop copying here ↑

---

## Step 4 — Add the skill to the project

1. Inside your project, go to **Settings → Skills**
2. Click **Add Skill**
3. Upload the `ai-news-filter.plugin` file you downloaded in Step 1
4. The skill is now active inside that project

---

## Step 5 — Connect your tools (optional but recommended)

The plugin works with just Claude's memory. But connecting these makes the filter much sharper:

| Tool | What it adds | How to connect |
|---|---|---|
| 📅 **Google Calendar** | Reads your last 7 days to infer focus areas | Claude.ai → Settings → Connected Apps → Google Calendar |
| 📝 **Notion** | Reads recent pages to identify active projects | Claude.ai → Settings → Connected Apps → Notion |

---

## Step 6 — Run it

Open a conversation inside the project and say any of these:

- `AI news`
- `/news`
- `What happened in AI this week?`
- `Run the news filter`

That's it. Claude will gather your context, search trusted sources, filter by relevance, and deliver 3-7 actionable news items.

---

## Step 7 — Schedule it weekly (optional)

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
