# 🔬 AI Update Research

> Stay ahead of AI trends with an automated signal-filtering digest from Reddit's top AI communities.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

AI Update Research is an AI-powered automation built in n8n that automatically:

- Monitors Reddit RSS feeds from r/LocalLLaMA, r/generativeAI, r/n8n, and r/GeminiAI every 6 hours
- Filters posts to only those published in the last 6 hours
- Uses GPT to separate signal from noise across three categories: Upstream (market trends), Midstream (operator builds), and Downstream (audience signals)
- Saves high-quality digests to Airtable for easy reference
- Composes and sends a formatted HTML email digest to your inbox

It's designed for AI builders, agency owners, and content creators who want to stay informed without drowning in noise.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 📡 **Multi-Source Ingestion** | Pulls from 4 Reddit AI communities simultaneously via RSS |
| ⏰ **Time-Based Filtering** | Only processes posts from the last 6 hours to keep content fresh |
| 🧠 **AI Signal Detection** | GPT categorizes posts as Upstream (trends), Midstream (builds), or Downstream (audience pain points) |
| 📊 **Airtable Archive** | Saves every digest with timestamp and status tracking |
| 📧 **Email Delivery** | Automatically formats and sends an HTML digest to your inbox |
| 🔄 **Scheduled Execution** | Runs every 6 hours on autopilot |

## 🏗️ Workflow Architecture

```
Schedule Trigger (6hr) → Fetch RSS Feeds (4 subreddits)
                              ↓
                    Merge → Filter Last 6 Hours → Format Content → Aggregate
                              ↓
                    GPT Signal Filter (Upstream/Midstream/Downstream)
                              ↓
              ┌───────────────┴───────────────┐
              ↓                               ↓
      Save to Airtable              Email Composer → Gmail
```

The workflow runs on a 6-hour schedule, pulls from multiple Reddit communities, filters for recency, then uses AI to extract only high-signal content before archiving and emailing.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [OpenAI](https://platform.openai.com) (for GPT signal filtering and email composition)
- [Airtable](https://airtable.com) (for digest storage)
- [Gmail](https://mail.google.com) (for email delivery via OAuth)
- [RSS.app](https://rss.app) (optional, for custom Reddit feeds)

### 2️⃣ Import the Workflow

1. Download `AI-Update-Research.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **OpenAI**: Add your API key for GPT access
2. **Airtable**: Create a base called "AI-Update-Research" with a table containing columns: `Time Stamp` (date), `Summary` (long text), `Status` (single select: New/Viewed)
3. **Gmail**: Authorize OAuth2 access and update the recipient email address in the "Send a message" node

### 4️⃣ Customize Your Sources

The default subreddits are:
- r/LocalLLaMA (local AI models)
- r/generativeAI (general AI discussion)
- r/n8n (automation community)
- r/GeminiAI (Google AI)

Add or swap RSS feeds in the fetch nodes to match your interests.

### 5️⃣ Adjust the Schedule

Default is every 6 hours. Modify the Schedule Trigger node to change frequency.

## 🧪 Example Use Cases

- **AI Agency Owners**: Stay current on tools and trends to advise clients
- **Content Creators**: Find high-signal topics for tutorials and threads
- **Indie Hackers**: Spot emerging opportunities before they go mainstream
- **Engineers**: Track practical builds and stack changes in the AI space

## 💡 Pro Tips

- The AI filter prompt uses three categories - tweak the system prompt to add your own focus areas
- Use Airtable's "Status" field to track which digests you've reviewed
- Add more RSS feeds for broader coverage (HackerNews, X lists, newsletters)
- The email digest is HTML-formatted - customize the emailComposer prompt for your preferred style

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, OpenAI GPT, Airtable, and Gmail
