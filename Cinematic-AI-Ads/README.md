# 🎬 Cinematic AI Ads Generator

> Turn a simple brand brief into a full cinematic video ad with AI-generated storyboards, images, and video.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## 🔍 Overview

Cinematic AI Ads is an AI-powered automation built in n8n that automatically:

- Accepts a brand brief via webhook (brand name, vibe, headlines, visual concept)
- Uses Gemini Pro to generate a detailed 6-8 scene cinematic storyboard
- Creates image prompts and video motion prompts for each scene
- Generates high-quality reference images using Kie.ai
- Produces cinematic video clips using Veo3 AI
- Tracks job status in Airtable for async processing
- Provides polling endpoints so your frontend knows when videos are ready

It's designed for agencies, marketers, and creators who want to produce high-quality video ads without expensive production teams.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 📝 **Brief-to-Storyboard** | Gemini Pro transforms your brand brief into a structured 6-8 scene cinematic storyboard |
| 🎨 **AI Image Generation** | Kie.ai generates photorealistic reference images from your scene prompts |
| 🎥 **AI Video Generation** | Veo3 turns your images + motion prompts into cinematic video clips |
| 🔄 **Async Processing** | Airtable tracks job status so long-running generations don't timeout |
| 📡 **Status Polling** | Built-in webhook endpoints let your frontend check when videos are done |
| 🔁 **Smart Retry Logic** | Automatic retry handling for failed generations |

## 🏗️ Workflow Architecture

```
Brief Webhook → Gemini Storyboard → Response (JSON scenes)

Image Webhook → Kie.ai Image Gen → Poll Status → Return Image URL

Video Webhook → Airtable Task → Veo3 Video Gen → Poll Status → Update Airtable → Done
            ↘ Return Task ID (async)

Status Webhook → Check Airtable → Return Video URL or "Processing"
```

The workflow is split into 4 independent modules: storyboard generation, image generation, video generation with state management, and status polling. This allows your frontend to orchestrate the full pipeline.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [OpenRouter](https://openrouter.ai) (for Gemini Pro access)
- [Kie.ai](https://kie.ai) (for image and video generation)
- [Airtable](https://airtable.com) (for job tracking)

### 2️⃣ Import the Workflow

1. Download `Cinematic-AI-Ads.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **OpenRouter**: Add your API key for Gemini Pro access
2. **Kie.ai**: Add your API key as an HTTP Header Auth credential
3. **Airtable**: Create a base called "Cinematic AI Ads" with a table "Video Processing Queue" containing columns: `Status` (single select: Todo/In progress/Done) and `videoURL` (text)

### 4️⃣ Set Up Your Webhooks

The workflow exposes 4 webhook endpoints:
- `POST /cinematic-ads` - Submit a brand brief, returns storyboard JSON
- `POST /CADI` - Submit an image prompt, returns image URL
- `POST /CADV` - Submit image URL + video prompt, returns task ID
- `GET /CADV-POLL?id={taskId}` - Check video status, returns video URL when done

### 5️⃣ Configure Your Frontend

Your app should:
1. POST brief to `/cinematic-ads` → get storyboard scenes
2. For each scene, POST to `/CADI` → get reference image
3. POST image + video prompt to `/CADV` → get task ID
4. Poll `/CADV-POLL?id=X` until you get the video URL

## 🧪 Example Use Cases

- **Ad Agencies**: Generate spec work and client pitches in minutes instead of days
- **E-commerce Brands**: Create product launch videos without hiring a production crew
- **Content Creators**: Produce cinematic B-roll and ads for sponsors
- **SaaS Companies**: Generate demo videos and promotional content at scale

## 💡 Pro Tips

- The storyboard prompt is highly customizable - adjust the scene count and style in the LLM Chain node
- Veo3 "fast" mode is used by default for speed; switch to standard for higher quality
- Use the Airtable base as a content library to review all generated assets
- The retry logic handles temporary API failures - check Airtable for stuck jobs

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, Gemini Pro, Kie.ai, Veo3, and Airtable
