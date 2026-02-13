# 💬 The "Comment" Content Engine

> Mine your audience's questions from TikTok, YouTube, and Reddit comments and transform them into viral Q&A content.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Comment Content Engine is an n8n automation that automatically:

- Accepts any TikTok, YouTube, or Reddit URL
- Scrapes comments using platform-specific APIs
- Extracts every legitimate question and objection using AI
- Generates punchy answer cards ready for Instagram Stories
- Creates 3-second verbal hooks for video replies
- Scores each question by lead conversion potential
- Saves content ideas and top pain points to Airtable

It's designed for creators who want to turn audience engagement into new content without manually reading hundreds of comments.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🎯 **Multi-Platform** | Works with TikTok, YouTube, and Reddit URLs |
| 🔍 **Comment Scraping** | Platform-specific scrapers get the full conversation |
| 🧠 **Question Extraction** | AI filters compliments and extracts real questions |
| ✍️ **Answer Cards** | Max 280 characters, ready for Instagram Stories |
| 🎬 **Video Hooks** | 3-second verbal hooks for reply videos |
| 📊 **Priority Scoring** | 1-10 score based on lead conversion potential |
| 😤 **Sentiment Tags** | Frustrated, Curious, Skeptical - know the vibe |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        PHASE 1: INPUT                               │
├─────────────────────────────────────────────────────────────────────┤
│  Form Trigger: Content URL                                          │
│  (TikTok, YouTube, or Reddit link)                                  │
│                              ↓                                      │
│                   Switch: Platform Router                           │
└─────────────────────────────────────────────────────────────────────┘
              ↓                    ↓                    ↓
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 2: COMMENT SCRAPING                        │
├─────────────────────────────────────────────────────────────────────┤
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐          │
│  │   TikTok     │    │   YouTube    │    │   Reddit     │          │
│  │   (Apify)    │    │   (API)      │    │   (API)      │          │
│  │              │    │              │    │              │          │
│  │  50 comments │    │ 100 comments │    │ All comments │          │
│  │  + replies   │    │  paginated   │    │              │          │
│  └──────────────┘    └──────────────┘    └──────────────┘          │
│         ↓                    ↓                    ↓                 │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐          │
│  │  Aggregate   │    │  Aggregate   │    │  Aggregate   │          │
│  │  TKComments  │    │  YTComments  │    │  RDTComments │          │
│  └──────────────┘    └──────────────┘    └──────────────┘          │
│                              ↓                                      │
│                   Merge: Consolidate Data                           │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                   PHASE 3: AI ANALYSIS                              │
├─────────────────────────────────────────────────────────────────────┤
│  LangChain: Insight Extraction (Gemini 3 Flash)                     │
│                              ↓                                      │
│  For Each Question Found:                                           │
│  • original_comment (raw text)                                      │
│  • platform (YouTube/TikTok/Reddit)                                 │
│  • refined_question (rephrased for clarity)                         │
│  • answer_card_text (280 chars max)                                 │
│  • hook_for_video_reply (3-second hook)                             │
│  • sentiment_tag (Frustrated/Curious/Skeptical)                     │
│  • priority_score (1-10)                                            │
│                              ↓                                      │
│  Summary: total questions, top pain point, missing sources          │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                      PHASE 4: STORAGE                               │
├─────────────────────────────────────────────────────────────────────┤
│  Save to Airtable:                                                  │
│  • Content URL                                                      │
│  • Top Pain Point                                                   │
│  • Q&A Items (linked table)                                         │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Apify](https://apify.com) (TikTok Comments Scraper actor)
- [YouTube API](https://console.developers.google.com) (Comments access via OAuth2)
- [Reddit API](https://www.reddit.com/prefs/apps) (OAuth2 for comments)
- [OpenRouter](https://openrouter.ai) (Gemini 3 Flash)
- [Airtable](https://airtable.com) (content idea storage)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Airtable

Create a base with a **Content URLs** table containing:
- Content URL (URL field)
- Top Pain Point (single line text)
- Content Analysis (linked records to Q&A items - optional)

### 4. Configure Credentials

1. **Apify**: Add your API key for TikTok comment scraping
2. **YouTube**: Authorize OAuth2 for YouTube API access
3. **Reddit**: Authorize OAuth2 for Reddit API access
4. **OpenRouter**: Add your API key for Gemini 3 Flash
5. **Airtable**: Authorize OAuth2 and update base/table IDs

## Example Output

```json
{
  "qa_engine_summary": {
    "total_questions_found": 8,
    "top_pain_point": "How to start without technical skills",
    "missing_sources": []
  },
  "qa_items": [
    {
      "original_comment": "but how do you even get started with this??",
      "platform": "TikTok",
      "refined_question": "What's the first step to building automations?",
      "answer_card_text": "Start with ONE workflow that saves you 1 hour/week. Don't try to automate everything. Pick your biggest time-suck and fix that first.",
      "hook_for_video_reply": "Here's what nobody tells beginners...",
      "sentiment_tag": "Frustrated",
      "priority_score": 9
    }
  ]
}
```

## Example Use Cases

- **Course Creators**: Find objections to address in sales pages
- **YouTubers**: Generate video reply content from high-value questions
- **Agency Owners**: Understand client pain points at scale
- **Coaches**: Create FAQ content from real audience struggles

## Pro Tips

- Run this on your top-performing content - those comments have the most engaged audience
- High priority scores (8-10) indicate strong lead conversion potential
- The "Frustrated" sentiment tag often reveals the deepest pain points
- Use the video hooks as actual first lines for TikTok replies
- Answer cards are sized for Instagram Stories - post directly
- Compliments like "Great video!" are automatically filtered out
- Run weekly on new content to build a content idea backlog

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Apify, YouTube API, Reddit API, OpenRouter (Gemini 3 Flash), and Airtable
