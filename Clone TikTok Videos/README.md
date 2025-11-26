# 🎬 TikTok Video Clone Engine

> An N8N automation that downloads any TikTok video without watermarks, analyzes it with AI, generates a detailed recreation prompt, and uses Wan 2.5 or Sora 2 to clone the video - then auto-posts to Instagram, TikTok, Twitter, and YouTube

## 📹 Video Walkthrough

["Here is a FULL DEMO"](https://www.youtube.com/watch?v=6ELszNyxUHY) with output examples and a step by step video walkthrough of how to setup the automation.

## ⚡ Overview

TikTok Video Clone Engine is an AI-powered automation built in n8n that automatically:

- Scrapes TikTok video pages to extract raw video URLs without watermarks
- Downloads the original video file with proper headers and cookies
- Analyzes the video frame-by-frame using Google Gemini 3 Pro
- Generates detailed 800-character prompts for AI video replication
- Creates clone videos using Wan 2.5 or Sora 2 (user selectable)
- Waits for video generation completion with polling logic
- Auto-uploads to Instagram Reels, TikTok, Twitter/X, and YouTube Shorts

It's designed for content creators, viral marketing teams, and automation agencies who want to replicate trending videos with AI-generated alternatives while maintaining the original structure, pacing, and concept.

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 🔓 **Watermark-Free Download** | Scrapes TikTok's HTML to extract the raw video URL before watermarks are applied. Uses session cookies for authenticated access. |
| 🧠 **AI Video Analysis** | Uses Google Gemini 3 Pro to analyze videos moment-by-moment, capturing visual details, audio characteristics, pacing, and voice-alike references. |
| ✍️ **Prompt Generation** | Creates precise 800-character prompts optimized for AI video generators with scene descriptions, timing, and audio cues. |
| 🎬 **Dual Model Support** | Choose between Wan 2.5 (720p, 9:16) or Sora 2 (portrait, 10 frames) via form selection before processing. |
| ⏱️ **Smart Polling** | Waits 3 minutes between status checks, validates generation success, and automatically retries on failure. |
| 📤 **Multi-Platform Upload** | Auto-uploads via Blotato to Instagram, TikTok, Twitter/X, and YouTube simultaneously. |

## 🔄 Workflow Architecture

Form Submission → Scrape TikTok Page → Extract Video URL → Download Original File → AI Analysis → Model Selection (Wan 2.5 or Sora 2) → Generate Video → Poll for Completion → Upload to Blotato → Multi-Platform Distribution (Instagram + TikTok + Twitter + YouTube)

The workflow uses custom JavaScript for HTML parsing, session cookie management, and JSON extraction to bypass TikTok's protection layers.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:

- [Google AI (Gemini)](https://aistudio.google.com/api-keys) (for video analysis)
- [Kie AI](https://kie.ai) (for Wan 2.5 and Sora 2 access)
- [Blotato](https://blotato.com/?ref=duncan) (for multi-platform social posting)

### 2️⃣ Import the Workflow

1. In n8n, click Import Workflow → upload the JSON file.
2. Set your credentials for Google Gemini, Kie AI, and Blotato in each node.
3. The workflow includes a form trigger - copy the webhook URL for submissions.

### 3️⃣ Configure Form Trigger

The workflow starts with a form that accepts:
- **URL field**: TikTok video URL (format: `https://www.tiktok.com/@username/video/ID`)
- **Video Model dropdown**: Choose between "Wan 2.5" or "Sora 2"

### 4️⃣ Connect Social Accounts

In the Blotato nodes, select your connected accounts:
- Instagram account ID
- TikTok account ID
- Twitter/X account ID  
- YouTube channel ID

### 5️⃣ Customize AI Prompt

Edit the "Analyze video" node to adjust the Gemini prompt:
```
Analyze this video moment by moment. Describe the video to an ai video generator 
so I can replicate this video exactly including the audio. If there's a notable 
person in the video, make sure to mention who they sound like. Output ONLY a prompt 
for an ai video generator. Prompt can be no more than 800 characters.
```

## 🧪 Example Use Cases

- **Content Creators**: Clone trending TikToks with AI-generated alternatives to avoid copyright issues while capitalizing on viral trends.
- **Marketing Agencies**: Create localized versions of successful video ads by replicating structure and pacing with brand-specific content.
- **Automation Operators**: Offer "viral video cloning" as a service - download, analyze, and regenerate trending content for clients.
- **Growth Hackers**: Test variations of high-performing videos by cloning the format and adjusting specific elements like voiceover or visuals.

## 📊 Key Workflow Steps

**Step 1: Scrape TikTok Page**
- Fetches full HTML with proper User-Agent headers
- Extracts session cookies for authenticated requests
- Parses `__UNIVERSAL_DATA_FOR_REHYDRATION__` script tag

**Step 2: Extract Video URL**
```javascript
const regex = /<script id="__UNIVERSAL_DATA_FOR_REHYDRATION__" type="application\/json">([\s\S]*?)<\/script>/;
const videoUrl = data?.__DEFAULT_SCOPE__?.["webapp.video-detail"]?.itemInfo?.itemStruct?.video?.playAddr;
```

**Step 3: Download Original File**
- Uses cookies from Step 1
- Sets Referer header to `https://www.tiktok.com/`
- Outputs binary video file without watermark

**Step 4: AI Analysis with Gemini**
- Analyzes video frame-by-frame
- Identifies pacing, transitions, voice characteristics
- Generates 800-char prompt for video generation

**Step 5: Model Selection & Generation**
- **Wan 2.5**: 9:16 aspect ratio, 10s duration, 720p resolution
- **Sora 2**: Portrait mode, 10 frames, watermark removal enabled

**Step 6: Polling & Upload**
- Waits 3 minutes between status checks
- Validates `state === "success"`
- Uploads to Blotato and distributes to all platforms

## 💡 Pro Tips

- Test with a single video first to verify scraping logic works with current TikTok HTML structure
- Monitor Kie AI credit usage - video generation can be expensive at scale
- Adjust the Gemini prompt to emphasize specific aspects (visual style, audio, pacing)
- Use Wan 2.5 for longer videos (up to 10s) and Sora 2 for high-quality shorter clips
- Check TikTok's robots.txt and terms of service before scraping at scale

## ⚠️ Important Notes

- **TikTok Structure Changes**: If the workflow stops working, TikTok may have changed their HTML structure. Update the JavaScript scraping logic in the "Scrape raw video URL" node.
- **Rate Limiting**: Avoid sending too many requests in rapid succession to prevent IP blocks.
- **Legal Considerations**: Ensure you have rights to replicate content and comply with platform policies.

---

## 🚀 Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[→ Join The Build Room for FREE!](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, Google Gemini, Wan 2.5, and Sora 2
