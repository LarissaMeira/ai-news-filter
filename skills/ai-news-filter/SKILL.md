---
name: ai-news-filter
description: "Personalized AI news curation with relevance filtering. ALWAYS use this skill when the user asks for: AI news, AI updates, 'what happened in AI', 'news digest', 'AI summary', 'what do I need to know today', 'run the news filter', '/news', 'AI curation', 'AI digest', 'AI briefing'. Also trigger when the user asks 'anything new in AI?', 'what came out today?', 'lab updates', 'what did OpenAI/Anthropic/Google launch'. DO NOT use for technical AI questions, tutorials, or opinions about specific tools."
---

# AI News Filter — Personalized AI News Curation

Inspired by Deborah Folloni's method: consume fewer AI news, but better ones, filtered by what actually matters for your projects and life.

## Principles

1. **Trusted sources only** — no generic aggregators or clickbait
2. **Relevance filter** — cross-reference news with the user's real context
3. **Test > accumulate** — highlight what's testable and actionable, not just informational

---

## Step 1 — Gather user context

Before searching for news, gather the context that will serve as the relevance filter. Use all available sources:

### 1a. Claude's memory
Two layers:
- **General memory**: everything you already know about the user (projects, field of work, tools they use, declared interests, role, company). This forms the base relevance profile.
- **Last 7 days of conversations**: search recent chats using the conversation search tool. Extract mentioned projects, tools tested, recurring questions, and topics where the user showed active interest. This captures the hot context — what's on the user's mind right now.

### 1b. ~~Calendar (next 7 days)
Fetch events for the next 7 days. Extract:
- Project names mentioned in event titles
- Meetings with clients or partners (indicate focus areas)
- Workshops, demos, or presentations scheduled (indicate hot topics)

### 1c. ~~Notes (last 14 days + last 7 days)
Two time windows:
- **Last 14 days**: search for pages indicating active projects and strategic direction. Look for pages with "project", "roadmap", "sprint", "OKR", "planning" in the title. This captures the big picture of what's in progress.
- **Last 7 days**: search for recently edited pages (any type). This shows where the user is putting energy right now, which tasks and documents are hot.

### Context synthesis
Compile an internal list (do not show to the user) with:
- **Active projects**: list of 3-8 projects/themes
- **Tools in use**: which platforms and models the user uses
- **Field of work**: sector, role, type of decisions they make
- **Declared interests**: topics the user has mentioned wanting to follow

If a source is unavailable (no calendar or notes connected), skip it and work with what you have. Memory alone is enough to build a useful filter.

---

## Step 2 — Search news from trusted sources

Search the web covering the 4 categories of trusted sources. Use 8-15 searches to cover the ground well. Searches should cover the **last 7 days** (unless the user requests a different period).

For the full list of default trusted sources, read `references/trusted-sources.md`.

### Search rules
- Prefer primary sources: official company blogs, direct posts from key people, published papers
- When a result looks relevant, use `web_fetch` to read the full content
- Discard results from low-quality sites, SEO aggregators, or republished content
- Include the date for each piece of news

---

## Step 3 — Filter by relevance

For each piece of news found, evaluate relevance using the context from Step 1:

**High relevance (always include)**
- Directly impacts an active project of the user
- Involves a tool the user already uses
- Opens a concrete opportunity for the user's work
- Is testable now (new feature, API, free tool)

**Medium relevance (include if few high-relevance items)**
- Related to the user's sector but no direct impact
- Important trend that may affect future decisions
- Relevant market movement (funding, acquisition, partnership)

**Low relevance (discard)**
- Generic news with no connection to the user's context
- Unconfirmed rumor
- Minor update with no practical impact
- Social media drama without substance

Target: deliver between **3 and 7 news items**, never more than 10.

---

## Step 4 — Deliver in chat

Write the response directly in chat, in the user's language, following this structure:

### Delivery format

Start with **one sentence** contextualizing the period and intensity (quiet day, busy week, etc.).

Then, for each piece of news, use this pattern:

**Short, direct title** — Source (e.g.: Anthropic Blog, Karpathy's post)
2-3 sentence summary explaining what happened and why it matters for the user specifically. If testable, say how.

### Writing rules
- Direct and practical tone, no sensationalism
- Always say **why that news matters for the user**, connecting to their project context
- If something is testable, include the path: "You can test this in [tool] by doing [action]"
- Don't repeat the same news from different angles
- Always paraphrase, never copy snippets from sources
- Cite the original source with link when available

### Closing
End with a short "To test" section listing the 1-3 most actionable items from the digest, if any.

---

## Example output

> Quiet week in AI. From ~30 news items I found, I filtered 4 that connect with what you're working on.
>
> **Anthropic launches streaming tool use** — Anthropic Blog
> You can now receive tool results in real-time via the API. This changes how you can structure the agent in [project name] — instead of waiting for the full response, you can show progress to the user. You can test this directly in your current setup.
>
> **Cursor adds native MCP integration** — Cursor Changelog
> Cursor now connects to MCP servers without manual configuration. Since you use Cursor daily, this simplifies the workflow with integrations you already have in Claude.
>
> **a16z publishes report on enterprise AI agents** — a16z Blog
> They mapped patterns that are working in production for enterprise agents. Relevant for the work you do with [user's area] — worth reading the adoption section.
>
> **Karpathy posts tutorial on efficient fine-tuning** — YouTube / X
> Practical walkthrough on LoRA fine-tuning on a budget. More educational than urgent, but aligned with what you were exploring in [project].
>
> **To test:**
> 1. Anthropic's streaming tool use (docs: [link])
> 2. Native MCP in Cursor (update to latest version)
