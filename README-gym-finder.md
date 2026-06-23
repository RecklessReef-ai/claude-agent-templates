# Gym Finder Agent

A sales prospecting agent that discovers gyms and fitness studios with group fitness classes and adds qualified leads to Notion.

## What It Does

- **Searches the web** for gyms, yoga studios, cycling studios, CrossFit boxes, etc. in a target city
- **Qualifies leads** by checking if they offer group fitness classes
- **Scores fit** (High/Medium/Low) based on class variety and focus
- **Adds to Notion** with structured data: name, address, class types, fit score, contact info
- **Deduplicates** against existing leads in the database

## Prerequisites

- Claude Code CLI
- Notion MCP integration with write access
- Web access for `WebSearch` and `WebFetch`

## Setup

1. Copy `gym-finder.md` to `~/.claude/commands/`
2. Connect Notion MCP to Claude Code
3. Replace placeholders in the file:
   - `[YOUR_NAME]` — your name
   - `[YOUR_PRODUCT_NAME]` — your product/service name
   - `[YOUR_CITY]` — default city to search (can override with args)

## Placeholders to Replace

| Placeholder | Description |
|-------------|-------------|
| `[YOUR_NAME]` | Your name |
| `[YOUR_PRODUCT_NAME]` | Your product/service being sold |
| `[YOUR_CITY]` | Default target city |

## Notion Database Schema

The agent creates a database called "Occupancy Platform — Gym Prospects" with:

| Field | Type | Description |
|-------|------|-------------|
| Studio Name | Title | Gym/studio name |
| City | Select | Target city |
| Address | Text | Full address |
| Website | URL | Studio website |
| Phone | Phone | Contact number |
| Class Types | Multi-select | yoga, HIIT, cycling, etc. |
| Fit Score | Select | High / Medium / Low |
| Status | Select | New Lead / Contacted / Demo Scheduled / Passed |
| Notes | Text | Additional info |
| Date Added | Date | When the lead was added |

## Usage

```bash
/gym-finder                    # Search default city (Chicago, IL or your setting)
/gym-finder "Austin, TX"       # Search Austin, TX
/gym-finder "Brooklyn, NY"     # Search Brooklyn, NY
/gym-finder "Miami, FL"        # Search Miami, FL
```

## Qualification Criteria

**Include** (add to Notion):
- Gyms with group fitness classes (yoga, cycling, HIIT, barre, pilates, CrossFit, kickboxing, dance, martial arts, boot camp)
- Studios with dedicated class schedules

**Exclude** (skip):
- Pure personal training gyms
- Physical therapy clinics
- Places with no group classes

## Fit Scoring

| Score | Criteria |
|-------|----------|
| **High** | Multiple group class types, dedicated schedule on website |
| **Medium** | Some group classes alongside personal training |
| **Low** | Primarily personal training, occasional group sessions |
