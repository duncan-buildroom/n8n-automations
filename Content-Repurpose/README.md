# 🔄 TikTok Content Repurpose Engine

> Automatically repurpose your TikTok videos to Instagram, Twitter/X, and YouTube Shorts with AI-generated captions.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

The Content Repurpose Engine is an AI-powered automation built in n8n that automatically:

- Monitors your TikTok RSS feed for new posts every hour
- Downloads videos without watermarks via RapidAPI
- Transcribes audio using OpenAI Whisper
- Generates SEO-optimized titles and descriptions using AI
- Backs up videos to Google Drive
- Distributes content to Instagram, Twitter/X, and YouTube Shorts simultaneously

It's designed for content creators and business owners who want to maximize their reach without spending hours manually reposting across platforms.

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 🔄 **Auto-Detection** | Monitors your TikTok RSS feed hourly and triggers on new content |
| 🎬 **Watermark-Free Downloads** | Uses RapidAPI to grab clean video files ready for cross-posting |
| 🎙️ **AI Transcription** | OpenAI Whisper converts your audio to text for caption generation |
| ✍️ **Smart Captions** | LLM generates clickbait-y titles (40 chars) and 200-word SEO descriptions |
| 💾 **Cloud Backup** | Automatically saves videos to Google Drive for your records |
| 📱 **Multi-Platform Posting** | Blotato handles simultaneous uploads to Instagram, Twitter/X, and YouTube |

## 🏗️ Workflow Architecture

```
RSS Feed Trigger → Download Video → Transcribe Audio → Generate Captions → Upload to Platforms
                                  ↘ Backup to Google Drive ↗
```

The workflow runs on a schedule (hourly polling) and processes each new TikTok through parallel paths for transcription/captioning and media backup before merging for final distribution.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [RSS.app](https://rss.app) (to generate a TikTok RSS feed)
- [RapidAPI](https://rapidapi.com) (TikTok video downloader API)
- [OpenAI](https://platform.openai.com) (for Whisper transcription)
- [OpenRouter](https://openrouter.ai) (for LLM caption generation)
- [Blotato](https://blotato.com) (for social media distribution)
- [Google Drive](https://drive.google.com) (for video backup)

### 2️⃣ Import the Workflow

1. Download `Content-Repurpose.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **RSS.app**: Create a TikTok feed and copy the feed URL
2. **RapidAPI**: Subscribe to a TikTok downloader API and get your API key
3. **OpenAI**: Add your API key for Whisper transcription
4. **OpenRouter**: Add your API key for LLM access
5. **Blotato**: Connect your Instagram, Twitter/X, and YouTube accounts
6. **Google Drive**: Authorize OAuth2 access and set your backup folder ID

### 4️⃣ Customize the Caption Prompt

Edit the `writeCaption` node to match your brand voice. The default prompt generates:
- A 40-character clickbait title with relevant keywords
- A 200-word SEO description with your standard CTA

## 🧪 Example Use Cases

- **Solo Creators**: Post once on TikTok, automatically appear everywhere else
- **Agency Owners**: Set up once per client, deliver consistent multi-platform presence
- **Course Creators**: Repurpose educational clips to build authority across channels
- **E-commerce Brands**: Turn product demos into platform-native content automatically

## 💡 Pro Tips

- Set up multiple RSS feeds if you manage several TikTok accounts
- Customize the caption prompt with your specific keywords and CTA
- Use the Google Drive backup as a content library for future repurposing
- Adjust the polling interval based on your posting frequency

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, OpenAI Whisper, OpenRouter, and Blotato
