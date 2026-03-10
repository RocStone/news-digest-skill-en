### Goal

Fetch approximately 100 latest stories from major tech news sites and communities OTHER than Hacker News, then filter and deeply decode the content most relevant to me. No shallow summaries — output must be a high-density intelligence briefing.

**Critical prohibition:** Absolutely NO Hacker News content — I have a separate pipeline for HN. Including HN here would cause severe content duplication!

### Execution Pipeline (strictly follow this flow, do NOT show interactive menus)

The following multi-step pipeline must be executed automatically without any user interaction:

1. **Fetch all sources in bulk**: Run the following commands to fetch all non-HN news sources (GitHub Trending, Product Hunt, 36Kr, Tencent News, WallStreetCN, V2EX, Weibo):
   ```bash
   python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source github --limit 25 --deep
   python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source producthunt --limit 15 --deep
   python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source 36kr --limit 15 --deep
   python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source tencent --limit 15 --deep
   python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source wallstreetcn --limit 15 --deep
   python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source v2ex --limit 15 --deep
   python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source weibo --limit 15 --deep
   ```
   Also use `last30days` to supplement with trending AI topics from Reddit/X/Web:
   ```bash
   python3 {baseDir}/deps/last30days/scripts/last30days.py "AI LLM tech trends" --emit=compact
   ```
   **Do NOT use `--source hackernews`! Do NOT show interactive menus! Execute commands directly!**
2. **Save raw data**: Write all source results into a single temp file under `tmp/news_raw/` (e.g., `tmp/news_raw/all_news.json`).
3. **Filter high-value stories**: Read the temp file, select the 30 most valuable stories using the Selection Criteria below. GitHub Trending should be presented as a separate table (at least 20 entries), not counted in the 30.
4. **Deep analysis by section**: Create a separate todo item for each source section, fetching, analyzing, and writing to the final file one section at a time. Every story must receive the full deep analysis specified in the Analysis Requirements below.

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
7. GitHub Trending must be presented as a table, at least 20 entries.

### Layout and Structure Requirements (critical)

The final Markdown output must be **strictly organized by source**, **absolutely NO mixing by theme**! Structure must follow:

```markdown
# YYYY-MM-DD Global Deep Insight Report (excluding Hacker News)

## GitHub Trending
### Full Trending Overview (Top 20)
| Repository | Description | Stars |
... (Table here)
### GitHub Selected Deep Insights
#### 1. [Project Name]
- **Source link**: [link text](URL)
1. **Core Insight** ... (followed by 6 analysis points)

## 36Kr
#### 1. [News Title]
- **Source link**: [link text](URL)
1. **Core Insight** ... (followed by 6 analysis points)

## Product Hunt
...and so on
```

### Analysis Requirements (strictly follow)

For each selected story, **provide the original article hyperlink (format: `- **Source link**: [title](URL)`, NEVER place it in a Header like `###`)**, then perform hardcore deep analysis using this framework:
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

**Most important directive!** Process by section with separate todo items (GitHub, Product Hunt, 36Kr, Tencent News, WallStreetCN, V2EX, Weibo, Reddit/X). Each todo item must deliver the high-quality deep analysis required by this document — skimming defeats the purpose!
