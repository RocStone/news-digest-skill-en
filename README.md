# News Digest Skill

AI/tech news deep-analysis workflow for Claude Code. All dependencies are bundled — install once, everything works.

## Features

- **/myhn** — Select 20 high-value stories from Hacker News, 7-dimension deep analysis
- **/news** — Global news (GitHub Trending, Product Hunt, 36Kr, etc.), 30 curated stories with deep analysis
- **/deep-dive** — Single-article deep analysis, maximizing cognitive gain

Each story is analyzed through: Core Facts/Insights, Deep Analysis, Community Discussion, Critical Reflection, One-Sentence Essence, Actionable Value, and more.

## Installation

```bash
git clone https://github.com/RocStone/news-digest-skill-en.git ~/.claude/skills/news-digest-skill-en
```

No extra dependencies to install. The following tools are bundled in `deps/`:
- [hn](https://clawhub.ai/gchapim/hackernews) (MIT-0) — Hacker News CLI
- [news-aggregator-skill](https://github.com/cclank/news-aggregator-skill) (MIT) — Multi-source news fetcher
- [last30days](https://github.com/mvanhorn/last30days-skill) (MIT) — Reddit + X + Web research

### Runtime Requirements

- Python 3.11+
- [uv](https://docs.astral.sh/uv/) (for the HN tool)

## Configuration

After installation, edit the "My Background" section in all three prompt files:

```
~/.claude/skills/news-digest-skill-en/prompts/hn-digest.md
~/.claude/skills/news-digest-skill-en/prompts/global-news-digest.md
~/.claude/skills/news-digest-skill-en/prompts/deep-dive.md
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

## Bundled Dependencies

| Tool | Author | License | Original Repo |
|------|--------|---------|---------------|
| hn | gchapim | MIT-0 | [clawhub.ai/gchapim/hackernews](https://clawhub.ai/gchapim/hackernews) |
| news-aggregator-skill | cclank | MIT | [github.com/cclank/news-aggregator-skill](https://github.com/cclank/news-aggregator-skill) |
| last30days | mvanhorn | MIT | [github.com/mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill) |

## License

MIT
