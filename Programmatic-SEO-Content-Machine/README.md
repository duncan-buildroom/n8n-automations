# 📝 Programmatic SEO Content Machine

> Generate multiple SEO-optimized articles from keywords with AI-powered web research and inline citations.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Programmatic SEO Content Machine is an AI-powered automation built in n8n that automatically:

- Accepts keywords via a web form and generates 2-5 unique article topics
- Uses Perplexity Sonar Pro Search to find trending content angles
- Researches each topic with real-time web search for latest stats and sources
- Writes comprehensive 1000-1500 word SEO articles with inline citations
- Saves completed articles with metadata to Airtable for publishing

It's designed for content marketers, bloggers, and agencies who need to produce high-quality SEO content at scale.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔍 **Trend Research** | Perplexity Sonar Pro finds trending angles for your keywords |
| 🎯 **Unique Angles** | Each article topic has a distinct perspective to avoid repetition |
| 📊 **Live Web Search** | Real-time research for 2024-2025 statistics and case studies |
| 📝 **Inline Citations** | Proper markdown links embedded in text, not bracketed numbers |
| 🏷️ **SEO Metadata** | Auto-generates meta descriptions and keyword lists |
| 💾 **Airtable Storage** | Organized article database ready for publishing |

## Workflow Architecture

```
Form Trigger (Keywords + Article Count)
              ↓
   Generate Article Topics (Perplexity Sonar Pro Search)
              ↓
         Parse JSON Topics
              ↓
        Split Into Individual Topics
              ↓
   ┌─────────┴─────────┐
   ↓                   ↓
Topic 1            Topic 2...
   ↓                   ↓
   └─────────┬─────────┘
              ↓
   Generate SEO Article (Per Topic)
   • Web Research (Perplexity Sonar)
   • Write 1000-1500 Word Article
   • Embed Inline Citations
              ↓
        Parse Article JSON
              ↓
        Save to Airtable
```

Topics are processed in parallel, with each article receiving dedicated web research.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [OpenRouter](https://openrouter.ai) (for Perplexity Sonar and GPT-4 Mini)
- [Airtable](https://airtable.com) (for article storage)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Airtable

Create a base called "Programmatic SEO Content Machine" with a table containing:
- `Article Title` (Single line text)
- `Article Text` (Long text)
- `Keywords` (Single line text)
- `Meta Description` (Single line text)
- `Created` (Created time - auto)

### 4. Configure Credentials

1. **OpenRouter**: Add your API key for access to Perplexity Sonar models
2. **Airtable**: Add your Personal Access Token and update the base/table IDs

### 5. Deploy the Form

1. Activate the workflow to generate the form URL
2. Share the URL or embed it in your internal tools
3. Enter keywords and select article count (2-5)

## Article Quality Features

The AI is instructed to:
- Write 1000-1500 words per article
- Use professional, authoritative tone
- Structure with ## main headings and ### subheadings
- Naturally incorporate target keywords
- Include inline markdown citations like `[Source Name](url)`
- Never use bracketed citation numbers like [1], [2]

## Example Output Structure

```json
{
  "title": "The Future of AI in Content Marketing",
  "metaDescription": "Discover how AI is revolutionizing content marketing...",
  "content": "## Introduction\n\nAccording to [Gartner](https://gartner.com)...",
  "keywords": "AI content marketing, automation, machine learning"
}
```

## Example Use Cases

- **Content Agencies**: Produce client blog posts at scale
- **SaaS Companies**: Generate product-related educational content
- **Affiliate Marketers**: Create keyword-targeted review articles
- **News Sites**: Cover trending topics with researched articles

## Pro Tips

- Use specific long-tail keywords for better article focus
- The "angle" feature ensures each article is unique even on similar topics
- Review and fact-check citations before publishing
- Add your brand voice by editing the system prompts
- Connect to WordPress or Ghost for direct publishing

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Perplexity Sonar (via OpenRouter), GPT-4 Mini, and Airtable
