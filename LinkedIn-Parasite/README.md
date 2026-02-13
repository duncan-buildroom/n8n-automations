# 🔄 LinkedIn Parasite

> Automatically scrape viral LinkedIn posts, rewrite them in your voice using AI knowledge bases, and generate custom images.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The LinkedIn Parasite is an AI-powered automation built in n8n that automatically:

- Scrapes LinkedIn posts from profiles you follow via Apify
- Stores posts with engagement metrics to track what's performing
- Rewrites posts in your unique voice using AI with personal knowledge bases
- Searches your YouTube transcripts and personal knowledge via Pinecone
- Performs live internet research to add fresh insights
- Generates custom images with GPT-image-1 (DALL-E)
- Saves ready-to-post content to Airtable for review and scheduling

It's designed for thought leaders who want to stay relevant by adding their perspective to trending topics without plagiarizing or copying content.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 📡 **Profile Monitoring** | Track multiple LinkedIn influencers and scrape their posts via Apify |
| 📊 **Engagement Tracking** | Stores comments, reactions, and shares to identify viral content |
| 🧠 **Knowledge Base Integration** | Pinecone vector stores for YouTube transcripts and personal expertise |
| 🔍 **Live Research** | GPT-4o-mini-search adds current data and trends to every post |
| ✍️ **Voice Matching** | AI rewrites content following your exact tone of voice guidelines |
| 🎨 **Custom Images** | GPT-image-1 generates headlines, bullet points, or flowchart visuals |
| 💾 **Content Pipeline** | Airtable tracks posts from scraped → content created → posted |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        PHASE 1: SCRAPING                            │
├─────────────────────────────────────────────────────────────────────┤
│  Get Profiles (Airtable) → Scrape Posts (Apify) → Dedupe & Filter   │
│                                   ↓                                 │
│                     Store to Airtable (Scraped Posts)               │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 2: CONTENT CREATION                        │
├─────────────────────────────────────────────────────────────────────┤
│  Get Unprocessed Posts → Get Tone of Voice → AI Agent               │
│                                                 ↓                   │
│              ┌──────────────────────────────────┼──────────────┐    │
│              ↓                                  ↓              ↓    │
│     YouTube KB (Pinecone)          Personal KB (Pinecone)   Research│
│              └──────────────────────────────────┴──────────────┘    │
│                                   ↓                                 │
│                     Generate Original Post (GPT-4o)                 │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 3: IMAGE GENERATION                        │
├─────────────────────────────────────────────────────────────────────┤
│  Create Image Prompt → Generate Image (DALL-E) → Upload (Drive)     │
│                                   ↓                                 │
│                     Save to Airtable (Ready to Post)                │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Apify](https://apify.com) (LinkedIn scraping actor)
- [OpenAI](https://platform.openai.com) (GPT-4o, GPT-image-1, embeddings)
- [Pinecone](https://pinecone.io) (vector database for knowledge bases)
- [Airtable](https://airtable.com) (content pipeline management)
- [Google Drive](https://drive.google.com) (image storage)

### 2. Import the Workflow

1. Download `LinkedIn-Parasite.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Airtable

Create a base with these tables:
- **Profiles**: LinkedIn profile URLs to monitor
- **Scraped Posts**: Post Text, Post URL, Author Name, # Comments, # Reactions, # Shares, Post Image, Status
- **Tone of Voice**: Your brand voice guidelines
- **Duncan Posts** (Your Posts): Post Text, Original Post, Post Image, Post URL, Status, Date Posted

### 4. Set Up Knowledge Bases

1. Create two Pinecone indexes: one for YouTube transcripts, one for personal knowledge
2. Upload your content to build the knowledge bases
3. Connect Pinecone credentials in n8n

### 5. Configure Credentials

1. **Apify**: Add your API key for LinkedIn scraping
2. **OpenAI**: Add your API key for GPT-4o, embeddings, and image generation
3. **Pinecone**: Add your API key and connect to your indexes
4. **Airtable**: Authorize OAuth2 and update base/table IDs
5. **Google Drive**: Authorize OAuth2 and set your image folder

## Example Use Cases

- **Thought Leaders**: Repurpose trending topics with your unique perspective
- **Agency Owners**: Build content libraries for client LinkedIn strategies
- **Consultants**: Stay visible by commenting on industry trends
- **Course Creators**: Transform viral posts into educational content

## Pro Tips

- Add profiles of competitors and industry leaders to monitor
- The AI is instructed to never copy - it creates fully original posts
- Use the engagement metrics to identify which scraped posts to prioritize
- Build your knowledge bases with your best content for authentic voice matching
- Review posts before publishing - the AI draft is a starting point
- The image generator creates headlines, bullet points, or flowcharts based on content type

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Apify, OpenAI GPT-4o, Pinecone, and Airtable
