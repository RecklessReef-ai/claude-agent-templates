# Social Manager Agent

A multi-platform social media manager that drafts, reviews, and publishes posts to Threads, LinkedIn, Twitter/X, Bluesky, and Pinterest — with automated video generation.

## What It Does

- **Fetches events** from Google Calendar and Luma
- **Generates promo videos** with text overlays using city footage
- **Drafts platform-optimized posts** with proper formatting, hashtags, and CTAs
- **Schedules posts** via Blotato API at optimal engagement times
- **Logs everything** for tracking and analytics

## Prerequisites

- Claude Code CLI
- [Blotato](https://blotato.com) account with API key
- Google Calendar MCP integration
- (Optional) Luma API key for event series
- (Optional) Google Drive with city videos for video generation

## Setup

1. Copy `social-manager.md` to `~/.claude/commands/`
2. Create config directory and file:
   ```bash
   mkdir -p ~/.claude/social-manager
   ```
3. Create `~/.claude/social-manager/config.json`:
   ```json
   {
     "blotato_api_key": "your-blotato-api-key",
     "owner": "[YOUR_NAME]",
     "location": "[YOUR_CITY]",
     "google_calendar_id": "[YOUR_GOOGLE_CALENDAR_ID]",
     "luma": {
       "api_key": "your-luma-api-key",
       "calendar_slug": "[YOUR_EVENT_SERIES]"
     },
     "accounts": {
       "threads": { "id": "", "handle": "" },
       "linkedin": { "id": "" },
       "twitter": { "id": "", "handle": "" },
       "bluesky": { "id": "", "handle": "" },
       "pinterest": { "id": "", "boardId": "" }
     }
   }
   ```
4. Replace all `[PLACEHOLDER]` values in the agent file

## Placeholders to Replace

| Placeholder | Description |
|-------------|-------------|
| `[YOUR_NAME]` | Your name |
| `[YOUR_CITY]` | Your city (e.g., "Austin, TX") |
| `[CITY]` | City name for hashtags |
| `[YOUR_PROFESSION]` | Your job title |
| `[YOUR_COMMUNITY_ORG]` | Local tech community name |
| `[YOUR_EVENT_SERIES]` | Your Luma calendar slug |
| `[YOUR_EVENT_AGGREGATOR_URL]` | Event listing site URL |
| `[YOUR_GOOGLE_CALENDAR_ID]` | Google Calendar ID |
| `[*_ACCOUNT_ID]` | Blotato account IDs (auto-populated on first run) |

## Usage

```bash
/social-manager              # Fetch, generate video, draft, review, publish
/social-manager novideo      # Skip video generation (text-only posts)
/social-manager event        # Promote a specific event across all platforms
/social-manager preview      # Show drafts only, don't publish
/social-manager log          # Show post history
```

## Platform Schedule

| Platform | Time (Local) | Post Type |
|----------|--------------|-----------|
| Threads | 9:00am | Conversational, hashtag-led |
| LinkedIn | 11:00am | Professional, story-driven |
| Twitter/X | 12:00pm | Punchy thread (3 tweets) |
| Bluesky | 1:00pm | Tech community energy |
| Pinterest | 8:00pm | Video pin with SEO hashtags |
