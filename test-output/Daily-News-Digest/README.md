# 📰 Daily News Digest

> Wake up to a curated email of buildable product ideas extracted from Reddit's AI and startup communities.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

Daily News Digest is an AI-powered automation built in n8n that automatically:

- Runs daily at 6am and fetches from 5 Reddit communities (r/MicroSaaS, r/generativeAI, r/n8n, r/ChatGPT, r/automation)
- Filters for posts from the last 6 hours
- Uses GPT to extract high-signal insights for founders and builders
- Identifies top signals, metrics, and recurring themes
- Composes a builder-focused email digest in Alex Hormozi's direct style
- Sends the digest to your inbox and archives to Airtable

It's designed for founders, indie hackers, and builders who want to spot opportunities without scrolling Reddit all day.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 📡 **5-Source Ingestion** | Pulls from MicroSaaS, GenerativeAI, n8n, ChatGPT, and Automation subreddits |
| ⏰ **Fresh Content Only** | Filters for posts from the last 6 hours to keep it current |
| 🧠 **Signal Extraction** | GPT identifies product patterns, founder lessons, pricing tactics, and metrics |
| 📧 **Builder-Style Email** | Alex Hormozi-inspired format: mechanism-first, no fluff, buildable ideas |
| 🔗 **Source Attribution** | Every idea links back to the original Reddit post |
| 🗄️ **Airtable Archive** | Saves digests with timestamps for future reference |

## 🏗️ Workflow Architecture

```
Schedule Trigger (6am Daily)
        ↓
┌───────┼───────────┬───────────┬───────────┐
↓       ↓           ↓           ↓           ↓
MicroSaaS  GenAI   n8n      ChatGPT   Automation
        ↓
    Merge RSS Feeds
        ↓
    Filter Last 6 Hours
        ↓
    Format Content → Aggregate
        ↓
    GPT Signal Extraction
        ↓
┌───────┴───────┐
↓               ↓
Airtable     Email Composer → Gmail
```

The workflow runs daily, pulls from 5 subreddits, filters for freshness, extracts insights with AI, then saves and emails the digest.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [OpenAI](https://platform.openai.com) (for GPT signal extraction and email composition)
- [Airtable](https://airtable.com) (for digest archival)
- [Gmail](https://mail.google.com) (for email delivery via OAuth)
- [RSS.app](https://rss.app) (optional, for custom Reddit feeds)

### 2️⃣ Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **OpenAI**: Add your API key for GPT access
2. **Airtable**: Create a base "AI-Update-Research" with columns: `Time Stamp` (date), `Summary` (long text), `Status` (New/Viewed)
3. **Gmail**: Authorize OAuth2 and update the recipient email in the "Send a message" node

### 4️⃣ Customize Sources

The default subreddits are:
- r/MicroSaaS (via RSS.app feed)
- r/generativeAI
- r/n8n
- r/ChatGPT
- r/automation

Swap or add RSS feeds to match your interests.

### 5️⃣ Adjust Timing

Default is daily at 6am. Modify the Schedule Trigger for different times or frequencies.

## 🧪 Example Use Cases

- **Indie Hackers**: Spot product ideas that already show demand before building
- **Agency Owners**: Stay current on automation trends to advise clients
- **Content Creators**: Find validated topics for tutorials and threads
- **Product Managers**: Track emerging user pain points and feature requests

## 💡 Pro Tips

- The signal extraction prompt prioritizes "buildable" ideas - customize for your focus area
- The email composer writes in Alex Hormozi style (mechanism-first, no fluff) - adjust the prompt for your preferred tone
- Add more subreddits by duplicating the RSS fetch nodes
- Use Airtable to track which digests you've acted on
- The 6-hour filter can be adjusted for more or less content volume

---

## 🚀 Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[→ Join The Build Room](https://www.skool.com/build-room)

---

Built with ❤️ using n8n, OpenAI GPT, Airtable, and Gmail
