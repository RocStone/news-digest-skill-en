---
name: news-digest-skill
description: "AI/tech news deep-analysis workflow. Fetches HN + global news, 7-dimension analysis framework, supports single-article deep dives."
---

# News Digest Skill

AI/tech news deep-analysis workflow with three sub-commands.

## Dependencies

Requires the following skills to be installed:
- `hn` — fetches Hacker News data
- `news-aggregator-skill` — fetches global news sources

## Sub-commands

### /myhn
Fetches the top 100 Hacker News stories, selects 20 for 7-dimension deep analysis.

Reads and executes `{baseDir}/prompts/hn-digest.md`.

### /news
Fetches news from all major sources except HN, selects 30 for hardcore deep analysis. Uses news-aggregator-skill to cover GitHub Trending, Product Hunt, 36Kr, Tencent News, WallStreetCN, V2EX, Weibo, etc.

Reads and executes `{baseDir}/prompts/global-news-digest.md`.

### /deep-dive <path or URL>
Performs deep analysis on a single document or link, maximizing cognitive gain. Covers core insights, positioning comparison, intuition building, non-obvious takeaways, and more.

Reads and executes `{baseDir}/prompts/deep-dive.md`.

## First-time Setup

After installation, edit the "My Background" section in all three files under `prompts/`. Replace the placeholders with your own information. The AI will use this to generate personalized analysis.

## Going Deeper

After reading the digest, if a particular story interests you, ask the AI to open the original link for further analysis, or use the `/deep-dive` command.
