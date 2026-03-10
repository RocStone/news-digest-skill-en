---
name: news-digest-skill
description: "AI/tech news deep-analysis workflow. Fetches HN + global news, 7-dimension analysis framework, supports single-article deep dives. All dependencies bundled — zero extra installs."
---

# News Digest Skill

AI/tech news deep-analysis workflow with three sub-commands. All dependency tools are bundled in `deps/`.

## Bundled Tools

The following tools are included in `{baseDir}/deps/` and do NOT need separate installation:

- **hn** — Hacker News CLI. Usage: `uv run {baseDir}/deps/hn/scripts/hn.py top -n 100`
- **news-aggregator-skill** — Multi-source news fetcher (GitHub Trending, Product Hunt, 36Kr, Tencent, WallStreetCN, V2EX, Weibo). Usage: `python3 {baseDir}/deps/news-aggregator-skill/scripts/fetch_news.py --source all --limit 15 --deep`
- **last30days** — Reddit + X + Web research tool. Usage: `python3 {baseDir}/deps/last30days/scripts/last30days.py "TOPIC" --emit=compact`

## Sub-commands

### /myhn
Fetches the top 100 Hacker News stories, selects 20 for 7-dimension deep analysis.

Reads and executes `{baseDir}/prompts/hn-digest.md`.

### /news
Fetches news from all major sources except HN, selects 30 for hardcore deep analysis. Uses the bundled news-aggregator-skill and last30days to cover GitHub Trending, Product Hunt, 36Kr, Tencent News, WallStreetCN, V2EX, Weibo, etc.

Reads and executes `{baseDir}/prompts/global-news-digest.md`.

### /deep-dive <path or URL>
Performs deep analysis on a single document or link, maximizing cognitive gain. Covers core insights, positioning comparison, intuition building, non-obvious takeaways, and more.

Reads and executes `{baseDir}/prompts/deep-dive.md`.

## First-time Setup

After installation, edit the "My Background" section in all three files under `prompts/`. Replace the placeholders with your own information. The AI will use this to generate personalized analysis.

Also customize the "Actionable Value" dimensions in `prompts/global-news-digest.md` to define what kinds of insights matter most to you.

## Going Deeper

After reading the digest, if a particular story interests you, ask the AI to open the original link for further analysis, or use the `/deep-dive` command.
