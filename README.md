# Claude Code Agent Templates

Reusable agent templates for [Claude Code](https://claude.ai/claude-code) — the CLI tool for AI-assisted software engineering.

These agents automate real workflows: social media publishing, video content pipelines, learning systems, and sales prospecting. Fork, customize the `[PLACEHOLDER]` values, and run.

## Agents

| Agent | Description | Docs |
|-------|-------------|------|
| **ai-tutor** | AI engineering tutor with spaced repetition learning | [README](README-ai-tutor.md) |
| **social-manager** | Multi-platform social media automation (Threads, LinkedIn, X, Bluesky, Pinterest) | [README](README-social-manager.md) |
| **video-manager** | High-volume TikTok & YouTube Shorts publishing pipeline | [README](README-video-manager.md) |
| **gym-finder** | Sales prospecting agent that finds leads and adds them to Notion | [README](README-gym-finder.md) |

## Quick Start

1. Install [Claude Code](https://claude.ai/claude-code)
2. Copy an agent file to `~/.claude/commands/`
3. Replace `[PLACEHOLDER]` values with your info
4. Run with `/agent-name`

## Common Placeholders

| Placeholder | Description |
|-------------|-------------|
| `[YOUR_NAME]` | Your name |
| `[YOUR_CITY]` | Your city (e.g., "Austin, TX") |
| `[YOUR_EMAIL]` | Your email address |
| `[YOUR_PROFESSION]` | Your job title |
| `[YOUR_GOOGLE_CALENDAR_ID]` | Google Calendar ID for event sources |
| `[*_ACCOUNT_ID]` | Platform account IDs (Blotato, etc.) |

## Prerequisites by Agent

| Agent | Requirements |
|-------|--------------|
| ai-tutor | Web access |
| social-manager | Blotato API, Google Calendar MCP, (optional) Luma API |
| video-manager | Blotato API + AI credits, Google Calendar MCP |
| gym-finder | Notion MCP, Web access |

## License

MIT — use freely, attribution appreciated.
