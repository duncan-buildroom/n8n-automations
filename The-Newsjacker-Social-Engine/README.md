# 📰 The Newsjacker Social Engine

> Hijack trending topics and turn them into niche-relevant hot takes with AI-generated visuals in your chosen tone.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Newsjacker Social Engine is an n8n automation that automatically:

- Scrapes live Twitter/X trends via Apify (1hr, 3hr, 6hr windows)
- Filters trends for relevance to your specific niche using AI
- Scrapes context tweets to understand what people are actually saying
- Writes "hot take" posts that bridge trends to your expertise
- Generates custom social media images matched to your chosen tone
- Saves ready-to-post content with visuals to Airtable

It's designed for content creators who want to stay relevant by commenting on trending topics without spending hours researching.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 📊 **Live Trend Scraping** | Apify Twitter Trends Scraper captures what's trending now |
| 🎯 **Niche Filtering** | AI selects only trends relevant to your topic (up to 5) |
| 🔍 **Context Research** | Scrapes latest tweets to understand the conversation |
| 🔥 **Hot Take Writer** | Gemini writes opinion posts in your specified tone |
| 🎨 **Visual Generator** | Creates square images styled to match sarcastic or professional tone |
| 💾 **Content Pipeline** | Saves posts and images to Airtable for review |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 1: TREND DISCOVERY                         │
├─────────────────────────────────────────────────────────────────────┤
│  Form Input (Niche + Tone) → Scrape Twitter Trends (Apify)          │
│                                   ↓                                 │
│         Get Trends Data → Format Strings → Aggregate List           │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 2: TOPIC FILTERING                         │
├─────────────────────────────────────────────────────────────────────┤
│  AI Selects Top Topics (Gemini 3 Pro)                               │
│                    ↓                                                │
│  Step 1: Find direct matches to niche (up to 5)                     │
│  Step 2: Emergency fallback - bridge high-profile event to niche    │
│                    ↓                                                │
│           Split Into Individual Topics → Loop                       │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 3: CONTEXT & COPYWRITING                     │
├─────────────────────────────────────────────────────────────────────┤
│  For Each Topic:                                                    │
│  Scrape Context Tweets (Apify) → Get 15 Latest → Aggregate          │
│                    ↓                                                │
│  AI Writes Hot Take (Gemini 3 Pro)                                  │
│  • Reads real conversation context                                  │
│  • Applies specified tone (sarcastic vs direct)                     │
│  • Creates niche-relevant opinion post                              │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 4: VISUALS & PUBLISHING                      │
├─────────────────────────────────────────────────────────────────────┤
│  Generate Metaphor Image (Gemini 3 Pro Image Preview)               │
│  • Sarcastic tone → Internet Ugly, Kitsch 3D, chaotic colors        │
│  • Direct tone → High-End Editorial, Swiss Design, monochrome       │
│                    ↓                                                │
│  Upload to Google Drive → Save Post + Image to Airtable             │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Apify](https://apify.com) (Twitter Trends Scraper + Twitter Search Scraper actors)
- [Google AI Studio](https://makersuite.google.com) (Gemini 3 Pro + Gemini 3 Pro Image Preview)
- [Google Drive](https://drive.google.com) (image storage)
- [Airtable](https://airtable.com) (content pipeline)

### 2. Import the Workflow

1. Download `The-Newsjacker-Social-Engine.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Airtable

Create a base with a table containing:
- Post (long text for the hot take)
- imagelink (URL to Google Drive image)
- Notes (optional for tracking)

### 4. Set Up Google Drive

1. Create a folder for Newsjacker images
2. Update the folder ID in the "Upload Image to GDrive" node

### 5. Configure Credentials

1. **Apify**: Add your API key for trend and tweet scraping
2. **Google Gemini**: Add your API key for text and image generation
3. **Google Drive**: Authorize OAuth2 for image uploads
4. **Airtable**: Authorize OAuth2 and update base/table IDs

## Tone Options

| Tone | Visual Style | Best For |
|------|-------------|----------|
| **Sarcastic and troll** | Internet Ugly, Kitsch 3D, neon colors, chaotic | Engagement bait, meme accounts, edgy brands |
| **Direct and clear** | High-End Editorial, Swiss Design, monochrome | Thought leadership, professional audiences |

## Example Use Cases

- **Tech Creators**: Comment on AI announcements with your coding perspective
- **Sports Commentators**: React to breaking news with hot takes
- **Marketing Agencies**: Newsjack trends for client social accounts
- **Finance Influencers**: Connect market news to your investment thesis

## Pro Tips

- The AI prioritizes direct matches first - only uses emergency fallback if zero matches found
- Context tweets give the AI real conversation data, not just headlines
- Image generation includes a 2-5 word punchline from your post
- Run during peak hours to catch fresh trends before they saturate
- Review posts before publishing - hot takes can be controversial
- The sarcastic tone creates intentionally "ugly" visuals that stand out in feeds

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Apify, Google Gemini 3 Pro, Google Drive, and Airtable
