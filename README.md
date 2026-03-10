# News Digest Skill

AI/tech news deep-analysis workflow for Claude Code.

## Features

- **/myhn** — Select 20 high-value stories from Hacker News, 7-dimension deep analysis
- **/news** — Global news (GitHub Trending, Product Hunt, 36Kr, etc.), 30 curated stories with deep analysis
- **/deep-dive** — Single-article deep analysis, maximizing cognitive gain

Each story is analyzed through: Core Facts/Insights, Deep Analysis, Community Discussion, Critical Reflection, One-Sentence Essence, Actionable Value, and more.

## Installation

```bash
npx skills add RocStone/news-digest-skill-en
```

### Dependency Skills

Install these before installing this skill:

```bash
npx skills add hn
npx skills add news-aggregator-skill
```

## Configuration

After installation, edit the "My Background" section in all three prompt files:

```
~/.agents/skills/news-digest-skill-en/prompts/hn-digest.md
~/.agents/skills/news-digest-skill-en/prompts/global-news-digest.md
~/.agents/skills/news-digest-skill-en/prompts/deep-dive.md
```

Replace the placeholders with your own information (job role, areas of focus, investment preferences, etc.). The AI will use this to generate personalized analysis.

Additionally, the "Actionable Value" section in `global-news-digest.md` should be customized. Default example dimensions are provided (research directions, open-source project ideas, interview prep, investment targets, etc.) — replace them with the value dimensions that matter most to you. This determines what angles the AI uses to extract actionable insights from each story.

## Usage

```
/myhn                        # Get today's HN news deep analysis
/news                        # Get global news deep analysis
/deep-dive ./path/to/file.md # Deep-dive into a specific document
/deep-dive https://example.com  # Deep-dive into a specific URL
```

## Output Examples

See the [daily-news-digest](https://github.com/RocStone/daily-news-digest) repo for sample outputs.

## License

MIT
