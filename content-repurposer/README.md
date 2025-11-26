# 🎬 TikTok Content Repurpose Engine

> An N8N automation that monitors your TikTok RSS feed, downloads videos, transcribes them with AI, generates platform-optimized captions, and auto-posts to Instagram, Twitter, and YouTube Shorts

## ⚡ Overview

TikTok Content Repurpose Engine is an AI-powered automation built in n8n that automatically:

- Monitors your TikTok RSS feed for new posts every hour
- Downloads the video file using TikTok API
- Transcribes audio content using OpenAI Whisper
- Generates SEO-optimized captions and clickbait titles using AI
- Uploads videos and posts simultaneously to Instagram, Twitter (X), and YouTube Shorts
- Maintains brand voice consistency across all platforms

It's designed for content creators, automation agencies, and solo operators who want to maximize reach by repurposing short-form content across multiple platforms without manual work.

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 📡 **RSS Monitor** | Polls TikTok RSS feed hourly to detect new video posts automatically. |
| 🎥 **Video Download** | Uses RapidAPI's TikTok downloader to fetch high-quality video files without watermarks. |
| 🎤 **AI Transcription** | Leverages OpenAI Whisper to transcribe video audio with high accuracy. |
| ✍️ **Smart Caption Writer** | Uses OpenRouter LLM to generate 40-char clickbait titles and 200-word SEO descriptions following Alex Hormozi-style copywriting principles. |
| 📤 **Multi-Platform Upload** | Auto-uploads via Blotato to Instagram Reels, Twitter/X, and YouTube Shorts simultaneously. |
| 🎯 **SEO Optimization** | Embeds keywords naturally: AI automations, n8n workflows, Make.com, ChatGPT, automation agency. |

## 🔄 Workflow Architecture

RSS Feed Monitor → Video Metadata Extraction → Video Download → AI Transcription + Media Upload → AI Caption Generation → Multi-Platform Distribution (Instagram + Twitter + YouTube)

Each step uses structured prompts, JSON schema validation, and error handling to maintain consistency and reliability across 24/7 automated operation.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:

- [RSS.app](https://rss.app) (for TikTok RSS feed generation)
- [RapidAPI](https://rapidapi.com) (TikTok Video Downloader API)
- [OpenAI API](https://platform.openai.com) (for Whisper transcription)
- [OpenRouter](https://openrouter.ai) (for LLM caption generation)
- [Blotato](https://blotato.com/?ref=duncan) (for multi-platform social posting)

### 2️⃣ Import the Workflow

1. In n8n, click Import Workflow → upload the JSON file.
2. Set your credentials for OpenAI, OpenRouter, RapidAPI, and Blotato in each node.
3. Edit the RSS Feed Trigger node to target your TikTok RSS feed URL.

### 3️⃣ Configure Your Accounts

In the Blotato nodes, select your connected accounts:
- Instagram account ID
- Twitter/X account ID  
- YouTube channel ID

### 4️⃣ Customize Caption Template

Edit the "writeCaption" node prompt to match your:
- Brand voice and tone
- Target keywords
- CTA preferences (currently set to "Comment 'AI' for free training")

Example prompt structure:
```
Video Description: {{ $('getVideo').item.json.description }}
Video Transcript: {{ $json.text }}

Generate a 40-char title starting with results language...
Generate a 200-word description following these rules...
```

## 🧪 Example Use Cases

- **Content Creators**: Automatically cross-post TikToks to grow on Instagram Reels, Twitter, and YouTube Shorts without manual uploads.
- **Automation Agencies**: Deploy for clients who need omnipresence across short-form video platforms with zero daily effort.
- **Solo Creators**: Scale content distribution while focusing creative energy on recording—let AI handle transcription, copywriting, and posting.
- **Personal Brands**: Maintain consistent posting schedules across platforms with SEO-optimized captions that drive discovery.

## 📊 Key Outputs

**Title Example:**
```
AI Automations That Build Themselves
```

**Description Example:**
```
Like + Comment "AI" and I will send you free training on how to build and sell AI automations.

Most people think building AI automations is hard. It's not. You just need the right system.

This workflow shows you how to:
- Monitor content feeds automatically
- Use AI to transcribe and optimize copy
- Deploy to multiple platforms in one click

Perfect for automation agencies, n8n operators, and solo creators who want to scale content without hiring a team.

The best part? It runs 24/7 with zero manual work.
```

## 💡 Pro Tips

- Test with a single video first before activating the hourly trigger
- Monitor API usage limits on OpenAI and RapidAPI
- Adjust caption length based on platform character limits
- Use Blotato's scheduling features for optimal posting times

---

Built with ❤️ using n8n, OpenAI, and OpenRouter
