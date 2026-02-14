# 📸 Instagram Scraper

> Scrape competitor Instagram Reels, analyze their content, and generate fresh video ideas with AI.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Instagram Scraper is an n8n automation that automatically:

- Pulls competitor Instagram usernames from your Airtable database
- Scrapes their latest Reels/Stories using Apify's Instagram API
- Captures key metrics: views, likes, comments, duration, hashtags, captions
- Uses GPT-4o to analyze each caption and generate 5 new content ideas
- Stores everything in Airtable with ideas linked to source content

It's designed for content creators and marketers who want to reverse-engineer what's working in their niche and generate endless content inspiration.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 📋 **Competitor Tracking** | Maintain a list of competitor accounts in Airtable |
| 🔍 **Reel Scraping** | Pull latest Reels with full metadata via Apify |
| 📊 **Engagement Metrics** | Capture views, likes, comments, and duration |
| 🏷️ **Hashtag Extraction** | Save hashtags used in each post |
| 🤖 **AI Idea Generator** | GPT-4o creates 5 fresh content ideas per video |
| 💾 **Organized Storage** | All data stored in Airtable for easy review |

## Workflow Architecture

```
Manual Trigger
       ↓
Get Competitors (Airtable)
       ↓
Loop Over Each Profile
       ↓
    ┌──────┴──────┐
    ↓             ↓
Scrape Reels   Generate Ideas
  (Apify)        (GPT-4o)
    ↓             ↓
Save Content   Clean Data
 (Airtable)       ↓
    ↓         Save Ideas
    └────→ Loop ←────┘
```

The workflow processes each competitor sequentially, scraping their content and generating ideas in batches.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Apify](https://apify.com) (for Instagram scraping)
- [OpenAI](https://platform.openai.com) (for GPT-4o)
- [Airtable](https://airtable.com) (for data storage)

### 2. Import the Workflow

1. Download `Instagram-Scraper.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **Apify**: Add your API key as an HTTP Header Auth credential
2. **OpenAI**: Add your API key for GPT-4o
3. **Airtable**: Create a base with two tables:
   - **Competitors**: Name (text) - Instagram usernames to scrape
   - **Scraped Content**: Profile, Caption, URL, Hashtags, Views, Likes, Comments, Duration, VideoID, Idea 1-5

### 4. Add Competitors

In your Airtable "Competitors" table:
1. Add Instagram usernames you want to track (without the @)
2. These are accounts whose content you want to analyze
3. Start with 3-5 accounts in your niche

### 5. Configure Scraping Options

In the scrapeProfiles node, you can adjust:
- `resultsLimit`: Number of posts to scrape per account
- `resultsType`: "stories", "posts", or "reels"

## The Idea Generation Framework

For each scraped video, GPT-4o generates 5 content ideas with:

- **Title**: Clear, compelling video title
- **Hook**: Punchy opening line or scroll-stopping hook
- **Description**: What the video will teach or include

The AI is prompted to create ideas for creators who teach AI, automation, personal branding, and business efficiency.

## Example Use Cases

- **Content Creators**: Find inspiration from top performers in your niche
- **Agency Owners**: Research competitor content strategies for clients
- **Brand Managers**: Track competitor Instagram activity and engagement
- **Social Media Managers**: Build a swipe file of proven content angles

## Pro Tips

- Focus on accounts with similar audience sizes for realistic benchmarks
- Run weekly to stay current with trending content styles
- Use the engagement metrics to identify what's actually performing
- The generated ideas are starting points - add your unique angle
- Filter your Airtable by highest engagement to find the best content to remix

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Apify, OpenAI GPT-4o, and Airtable
