# AI Tutor Agent

A personal AI engineering tutor that gathers the latest hands-on AI content from the web and teaches it through interactive sessions with spaced repetition.

## What It Does

- **Gathers** new AI engineering content (agents, prompting, RAG, evals, LLM APIs) via web search
- **Teaches** concepts interactively: explain → worked example → quiz → grade
- **Tracks mastery** using spaced repetition (new → learning → reviewing → mastered)
- **Fills CS gaps** when foundational concepts come up (data structures, networking, async, etc.)

## Prerequisites

- Claude Code CLI
- Web access for `WebSearch` and `WebFetch`

## Setup

1. Copy `ai-tutor.md` to `~/.claude/commands/`
2. Create the state directory:
   ```bash
   mkdir -p ~/.claude/ai-tutor
   ```
3. Replace placeholders in the file:
   - `[YOUR_NAME]` — your name
   - `[CITY]` — your city
   - `[YOUR_PROFESSION]` — your job title/role

## State Files

The agent creates and maintains:
- `~/.claude/ai-tutor/config.json` — focus areas, search queries, session limits
- `~/.claude/ai-tutor/knowledge-base.md` — all concept cards
- `~/.claude/ai-tutor/progress.json` — per-card mastery tracking
- `~/.claude/ai-tutor/session-log.md` — session history

## Usage

```bash
/ai-tutor                # Interactive session: teach + quiz on new and due cards
/ai-tutor gather         # Search web for new AI eng content, write cards (no quiz)
/ai-tutor gather auto    # Same as gather, non-interactive (for cron/loops)
/ai-tutor review         # Spaced repetition pass on due cards only
/ai-tutor preview        # Show what's new and due today (read-only)
/ai-tutor log            # Show session history + mastery summary
```

## Customization

Edit the `config.json` to adjust:
- `search_queries` — what topics to search for
- `max_new_per_session` — how many new cards per teaching session
- `max_reviews_per_session` — how many review cards per session
