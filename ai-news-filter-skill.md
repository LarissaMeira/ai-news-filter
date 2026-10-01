---
name: ai-news-filter
description: "Personalized AI news curation with relevance filtering. Activate when the user asks for: AI news, AI updates, 'what happened in AI', news digest, /news, AI briefing. Also trigger on 'anything new in AI?', 'what came out today?', 'lab updates'. Do not use for technical AI questions or tutorials."
---

## Principles
1. Trusted sources only — no generic aggregators or clickbait
2. Relevance filter — cross-reference news with the user's real context
3. Test > accumulate — highlight what's testable and actionable
4. Substance > headline — every item needs enough real detail (facts, numbers, context) that the user doesn't have to click through to understand what happened
5. Language match — always write the output in the same language the user wrote their request in, regardless of what language the sources are in

## Step 1 — Gather user context
Two layers of Claude's memory:
- General memory: projects, field of work, tools, interests, role, company
- Last 7 days of conversations: recent projects, tools tested, active interests

Calendar (last 7 days): project names, client meetings, workshops, demos

Notion (two layers):
- list-recent-pages: what's on the user's radar right now
- notion-search with last_edited_date_range (14 days): pages with project, roadmap, sprint, OKR, planning
- notion-search with last_edited_date_range (7 days): recently edited pages (any type)

Granola (last 7 days):
- Recent meeting transcripts: Summary, topics discussed, decisions made, client names mentioned, action items identified. This captures context from live conversations that doesn't appear in notes or calendar titles.

Gmail (last 7 days, personal context only, not a news source):
- Recent threads: sender/recipient names, subject lines, and active conversation topics. Skip newsletters, automated notifications, and marketing email, focus on real threads with clients, partners, or collaborators. This captures client names and active work threads that might not show up in Calendar or Notion.

If a source isn't connected or a tool call fails, skip it silently and continue with whatever context is available — never stop the whole process over one missing source.

## Step 2 — Search trusted sources (8-15 searches)
Search for the period specified by the user. If no period is given, use the default from the project instructions.

Labs: OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral, Cohere, Stability AI, Midjourney
Apps: Lovable, ElevenLabs, Cursor, Replit, Higgsfield, Vercel (v0), Perplexity, Notion AI, Canva AI, Figma AI
Funds: Sequoia, a16z, Y Combinator, Lightspeed, Accel
Key People: Elena Verna, Boris Cherny, Andrej Karpathy, Tariq Shihipar, Sam Altman, Dario Amodei, Garry Tan, Satya Nadella, Jensen Huang, Demis Hassabis

Rules: primary sources only, use web_fetch for full content, discard SEO aggregators. When a result is thin, fetch the primary source directly and pull the real numbers, quotes, and context, don't settle for a headline-level summary.

## Step 3 — Filter by relevance
High (always include): impacts active project, involves tools in use, testable now
Medium (include if few high): related to sector, important trend, market movement
Low (discard): generic, unconfirmed, minor update, social media drama

Target: deliver items according to the target defined in the project instructions. If no target is defined, default to 8-15 items for a 7-day period, scaled proportionally for shorter or longer periods. Never include low-relevance items just to fill the target.

## Step 4 — Deliver as a PDF report
Build a single PDF report, not a chat-only listing. Use whatever PDF-generation capability is available in the environment (a PDF-authoring skill, a document tool, etc.) rather than improvising with raw text — the report needs real formatting, not a wall of markdown pasted into a page. Structure, in this order:

1. **Header and context**: title, period covered, one paragraph summarizing the shape of the week.
2. **The news, grouped by relevance (High, then Medium)**. Each item gets real substance, not a 2-3 sentence blurb: what actually happened, the concrete numbers/facts/quotes behind it, why it matters, and how to test it if testable. A reader should understand the story without needing to open the source. Right on the item itself — on the title or source name, not buried elsewhere — add a clickable hyperlink to the original article, so a reader who wants more can jump straight there mid-read instead of hunting for it in a table at the end.
3. **What to apply**: 3-6 concrete actions, placed after the news. Each one names the specific tool or project it touches and a concrete next step, not generic advice like "keep an eye on this."
4. **Sources**: a table listing every item with a clickable hyperlink to its source, as a recap — this is a backup reference, not the only place a link appears.

Every link in the PDF, inline and in the table, must be a real clickable hyperlink (not just visible URL text) — check that the PDF tool you use actually embeds the link as a clickable annotation rather than printing it as plain text. Deliver the PDF as an actual file sent to the user, not just described in text — the task isn't done until the file itself has been handed over. Never paste the report as markdown in the chat window instead. Write the whole report in the same language the user's request was written in, even when the source articles are in a different language.
