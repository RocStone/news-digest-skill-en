### Goal

Fetch approximately 100 stories from Hacker News and other major tech news sources, then select 20 for in-depth analysis relevant to my interests. Do not skimp on tokens — completing this task thoroughly is the top priority.

### My Background
<!-- Replace the content below with your own information -->
<!-- The AI will use this to generate personalized analysis in the "Takeaways for Me" section -->
- Your job role (e.g., backend engineer, AI grad student, product manager...)
- What you currently focus on (e.g., job search, tech stack decisions, startup ideas...)
- Investment preferences (if any)
- Any other personal context you want the AI to consider during analysis

### Selection Criteria

From the ~100 stories, prioritize the following categories:

1. **AI Industry Trends** — News directly related to the AI job market, open-source ecosystem, and technology trends
2. **High-Impact Papers** — Research work likely to have significant future impact
3. **Financial Markets** — Important movements and analysis in US equities
4. **AI Best Practices** — Experiences and methodologies for using AI more effectively
5. **Mental Models** — Thinking frameworks and cognitive models worth learning

### Execution Pipeline (strictly follow this flow for depth and quality)

To prevent context overload from degrading analysis quality as more articles are processed, the following multi-step pipeline is mandatory:

1. **Fetch bulk data**: Use the bundled HN tool (`uv run {baseDir}/deps/hn/scripts/hn.py top -n 100`) to fetch the top 100 Hacker News stories and write the raw list to a temp file (e.g., `tmp/hn_top_100.md`).
2. **Select high-value stories**: Based on the temp file, select 20 candidate stories using the Selection Criteria above.
3. **Fetch detailed content and top comments**: Write and run a Python script that uses the Hacker News API (`https://hacker-news.firebaseio.com/v0/item/{id}.json`) to fetch detailed content and top-rated comments for all 20 stories, generating an independent `.md` task file for each story in `tmp/hn_tasks/`.
4. **Independent parallel analysis (Sub-agents)**: Process the 20 task files using `generalist` sub-agents. Each sub-task receives only the single story's content plus the analysis requirements below, producing an independent deep-analysis report (e.g., `*_out.md`) in a clean context. This ensures each story gets full analytical attention without context pollution.
5. **Merge into final report**: Write a script to read all 20 independent reports, merge them into one complete Markdown file, and write it to the output path specified below.

### Analysis Requirements

For each selected story, fetch its top-rated Hacker News comments and analyze using this framework:

1. **Core Facts** — First-principles breakdown: what is this really about? This section must be detailed enough that I can grasp the essence without missing critical information.
2. **Deep Analysis** — Why does this matter? What is the underlying logic?
3. **Top Community Discussion** — Summarize high-rated comments from the HN thread: what are people debating? What controversies exist? How do insiders view this?
4. **Future Impact** — How will this develop? What potential effects on the industry/market?
5. **Critical Reflection** — Is there overhype? Is the source spinning a narrative? Do the conclusions hold up under scrutiny?
6. **One-Sentence Essence** — After all analysis, boil it down to one brutally honest sentence about its true technical/business reality. Use the format: "At its core, this is basically..." Note: be objective, neutral, and insightful — aim to reveal the core mechanism or real value, not to dismiss or mock.
7. **Takeaways for Me** — What specific implications does this have for my career, open-source project choices, or investment decisions?

### Output Requirements

- Analysis quality must be high enough that I never need to read the original article or comments
- Prioritize conclusions and insights over information listing
- For controversial content, explicitly flag uncertainty — do not present opinions as established facts
- Every story must include hyperlinks in appropriate places (e.g., first line below the heading), but NEVER on headings themselves (h2/h3/h4) — this causes overly long titles when referenced. Important!
- Output file path: `news/{current date} HackNews.md` (e.g., `2026-03-04 HackNews.md`), adjustable as needed
- Explain key abbreviations and technical terms
