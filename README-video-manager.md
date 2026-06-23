# Video Manager Agent

A high-volume video publishing agent for TikTok and YouTube Shorts that turns event content into multiple posts using AI-generated videos and rotating caption templates.

## What It Does

- **Multiplies content**: Each event generates 4 posts across 4 days (awareness → building → urgency → FOMO)
- **Generates AI videos**: Creates unique promotional videos via Blotato's AI Story Video templates
- **Rotates captions**: Uses template library with dynamic variables to avoid repetition
- **Manages hashtags**: Rotates through hashtag sets (A → B → C) to maximize reach
- **Schedules at scale**: Up to 8 TikTok + 2 YouTube posts per day

## Prerequisites

- Claude Code CLI
- [Blotato](https://blotato.com) account with:
  - API key
  - Connected TikTok account
  - Connected YouTube account
  - AI Story Video credits
- Google Calendar MCP integration

## Setup

1. Copy `video-manager.md` to `~/.claude/commands/`
2. Create config directory:
   ```bash
   mkdir -p ~/.claude/video-manager
   ```
3. Create `~/.claude/video-manager/config.json`:
   ```json
   {
     "blotato_api_key": "your-blotato-api-key",
     "owner": "[YOUR_NAME]",
     "location": "[YOUR_CITY]",
     "google_calendar_id": "[YOUR_GOOGLE_CALENDAR_ID]",
     "accounts": {
       "youtube": { "id": "", "playlistId": "" },
       "tiktok": { "id": "" }
     }
   }
   ```
4. Replace all `[PLACEHOLDER]` values in the agent file

## Placeholders to Replace

| Placeholder | Description |
|-------------|-------------|
| `[YOUR_NAME]` | Your name |
| `[YOUR_CITY]` | Your city |
| `[CITY]` | City name for captions/hashtags |
| `[YOUR_INCOME_GOAL]` | Your revenue target (or remove this line) |
| `[YOUR_GOOGLE_CALENDAR_ID]` | Google Calendar ID for events |
| `[YOUR_EVENT_AGGREGATOR_URL]` | Event listing site for CTAs |
| `[YOUTUBE_ACCOUNT_ID]` | Blotato YouTube account ID |
| `[TIKTOK_ACCOUNT_ID]` | Blotato TikTok account ID |

## Content Multiplication Strategy

| Post # | Timing | Caption Angle | Urgency |
|--------|--------|---------------|---------|
| Post 1 | 5-7 days out | "Coming up this weekend..." | Low |
| Post 2 | 2-3 days out | "Only X days away..." | Medium |
| Post 3 | 1 day out | "Tomorrow in [CITY]..." | High |
| Post 4 | Day of | "Happening TODAY..." | Maximum |

## Usage

```bash
/video-manager              # Generate videos, draft posts, review, publish
/video-manager auto         # Skip approval, publish immediately (for cron)
/video-manager preview      # Show today's queue without publishing
/video-manager log          # Show post history
/video-manager novideo      # Skip video generation (both platforms skipped)
```

## Daily Posting Schedule

**TikTok** (up to 8/day): 7am, 7:30am, 12pm, 12:30pm, 5pm, 5:30pm, 9pm, 9:30pm

**YouTube Shorts** (2/day): 8am (today's event), 3pm (tomorrow's event)
