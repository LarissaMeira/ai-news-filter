---
name: ai-news-filter
description: "Personalized AI news curation with relevance filtering. Activate when the user asks for: AI news, AI updates, 'what happened in AI', news digest, /news, AI briefing. Also trigger on 'anything new in AI?', 'what came out today?', 'lab updates'. Do not use for technical AI questions or tutorials."
---

## Principles
1. Trusted sources only — no generic aggregators or clickbait
2. Relevance filter — cross-reference news with the user's real context
3. Test > accumulate — highlight what's testable and actionable

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

## Step 2 — Search trusted sources (8-15 searches)
Search for the period specified by the user. If no period is given, use the default from the project instructions.

Labs: OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral, Cohere, Stability AI, Midjourney
Apps: Lovable, ElevenLabs, Cursor, Replit, Higgsfield, Vercel (v0), Perplexity, Notion AI, Canva AI, Figma AI
Funds: Sequoia, a16z, Y Combinator, Lightspeed, Accel
Key People: Elena Verna, Boris Cherny, Andrej Karpathy, Tariq Shihipar, Sam Altman, Dario Amodei, Garry Tan, Satya Nadella, Jensen Huang, Demis Hassabis

Rules: primary sources only, use web_fetch for full content, discard SEO aggregators

## Step 3 — Filter by relevance
High (always include): impacts active project, involves tools in use, testable now
Medium (include if few high): related to sector, important trend, market movement
Low (discard): generic, unconfirmed, minor update, social media drama

Target: deliver items according to the target defined in the project instructions. Never include low-relevance items just to fill the target.

## Step 4 — Deliver in chat
One sentence contextualizing the period. Then for each news:
**Title** — Source
2-3 sentences on what happened + why it matters for the user. If testable, say how.

End with "To test" section: most actionable items.
