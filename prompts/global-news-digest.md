### Goal

Use the bundled tools (especially `news-aggregator-skill` at `{baseDir}/deps/news-aggregator-skill/` and `last30days` at `{baseDir}/deps/last30days/`) to fetch approximately 100 latest stories from major tech news sites and communities OTHER than Hacker News.
**Critical prohibition:** Absolutely NO Hacker News content — I have a separate pipeline for HN. Including HN here would cause severe content duplication! When using `news-aggregator-skill`, explicitly exclude the HN data source. When using `last30days`, also exclude HN-related results.

From these, filter and deeply decode the content most relevant to me. No shallow summaries — output must be a high-density intelligence briefing.

### My Background
<!-- Replace the content below with your own information -->
<!-- The AI will use this to generate personalized analysis in the "Actionable Value" section -->
- Your job role (e.g., backend engineer, AI grad student, product manager...)
- What you currently focus on (e.g., job search, tech stack decisions, startup ideas...)
- Investment preferences (if any)
- Information preferences: prioritize topics you care about, but also cover unfamiliar areas to avoid filter bubbles. No sports or entertainment news
- Any other personal context you want the AI to consider during analysis

### Selection Criteria

From the ~100 stories, quality over quantity — select the 30 most valuable (prioritize these categories):

1. **AI Industry Trends** — News directly related to the AI job market, open-source ecosystem, and technology trends
2. **High-Impact Papers** — Research work likely to have significant future impact
3. **Financial Markets** — Important movements and analysis in US equities
4. **AI Best Practices** — Experiences and methodologies for using AI more effectively
5. **Mental Models** — Thinking frameworks and cognitive models worth learning
6. **Important**: Do NOT preset keywords — this creates filter bubbles. Read ALL stories first, then filter based on my background. To save tokens, you only need to read titles to judge relevance.
7. GitHub Trending must be presented as a table, at least 20 entries

### Analysis Requirements (strictly follow)

For each selected story, **provide the original article hyperlink**, then perform hardcore deep analysis using this framework:
1. **Core Insight** — One sentence that cuts to the heart: what fundamental problem does this solve?
2. **Deep Analysis and Underlying Logic** — Explain the technical trade-offs, why it works, or whose lunch it is eating. No surface-level news rehashing — use first-principles reasoning.
3. **Intuition Building** — Use the most fitting analogy (e.g., comparing speculative decoding to senior-junior code review) to help me build instant technical intuition.
4. **Critical Reflection and Blind Spots** — Incorporate sharp commentary and genuine insights from different communities. Point out the thorns — overhype, performance traps, logical flaws.
5. **One-Sentence Essence** — After all analysis, boil it down to one brutally honest sentence. Use the format: "At its core, this is basically..." (to cut through the packaging and see if it is a wrapper or the real deal). Critical: stay objective and neutral! Do not dismiss everything as worthless junk just to sound edgy. Objectively assess its real position and practical value in the current technology landscape — strip away the hype, but without cynical sneering.
6. **Actionable Value** — This is the most critical part. Directly identify how this story can translate into concrete action for me.
   <!-- Replace the dimensions below with your own "high-value action directions" -->
   <!-- Example dimensions (add/remove based on your needs): -->
   <!-- - Research directions or paper ideas -->
   <!-- - Entry points for high-star GitHub open-source projects -->
   <!-- - Interview topics for competitive advantage -->
   <!-- - Specific investment targets or pitfalls to avoid -->
   <!-- - Product inspiration / startup opportunities -->
   <!-- - Tech stack decision references -->
   - List the value dimensions that matter most to you here

### Output Quality Standards

- Never skim the surface: analysis must be deep enough to produce genuine insights — turn it into a weapon in my mental arsenal.
- Information completeness: must include original article hyperlinks (for easy reference). But NEVER put links on headings (h2/h3/h4 of any level)! This causes overly long titles when referenced. Important!
- Maximize cognitive gain: after reading this report, I should have zero need to visit the original sites to absorb 100% of the core value.

### Output
Report file path: `./news/{YYYY-MM-DD Global News}.md`, adjustable as needed.

**Most important directive!** If there are multiple sections (e.g., GitHub, Product Hunt, Tencent News), create separate todo items for each, fetching news, analyzing, and writing to the file one section at a time. Each todo item must deliver the high-quality analysis required by this document — skimming defeats the purpose. In practice, there should be many sections, because your skills cover many data sources — I want content from ALL of them!
