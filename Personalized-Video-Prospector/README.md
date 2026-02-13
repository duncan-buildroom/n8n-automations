# 🎬 Personalized Video Prospector

> Generate personalized AI avatar videos for sales outreach at scale using lead data and talking head technology.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Personalized Video Prospector is an AI-powered automation built in n8n that automatically:

- Scrapes leads from Apollo/ZoomInfo-style databases via Apify
- Enriches leads with full LinkedIn profile data
- Generates hyper-personalized sales scripts using Gemini 3 Pro
- Creates natural voiceovers with ElevenLabs via WaveSpeed
- Produces talking head avatar videos with AI lip-sync
- Delivers finished videos to Google Drive with status tracking

It's designed for sales teams who want to stand out with personalized video outreach without recording each video manually.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔍 **Lead Scraping** | Apify pulls verified leads from Apollo/ZoomInfo with emails and job data |
| 📊 **LinkedIn Enrichment** | Full profile scraping adds experience, certifications, awards, and more |
| 🎯 **Smart Hook Finding** | AI identifies unique facts (patents, awards, volunteering) for personalization |
| ✍️ **Script Generation** | Gemini writes emotional scripts with audio tags and emphasis markers |
| 🎙️ **Voice Synthesis** | ElevenLabs creates natural voiceovers with emotion and pauses |
| 🎥 **Avatar Videos** | WaveSpeed InfiniteTalk generates talking head videos with lip-sync |
| 📤 **Auto-Delivery** | Uploads to Drive and updates your lead sheet with video links |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                     PHASE 1: LEAD SCRAPING                          │
├─────────────────────────────────────────────────────────────────────┤
│  Config (# Leads) → Run Scraper (Apify) → Save to Google Sheets     │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 2: ENRICHMENT & VALIDATION                   │
├─────────────────────────────────────────────────────────────────────┤
│  Fetch Ready Leads → LinkedIn Enrichment (Apify) → Validate Data    │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                   PHASE 3: AI SCRIPT & AUDIO                        │
├─────────────────────────────────────────────────────────────────────┤
│  Generate Script (Gemini) → ElevenLabs Audio (WaveSpeed)            │
│                                   ↓                                 │
│                     Wait → Poll → Audio Complete?                   │
│                                   ↓ (loop until ready)              │
└─────────────────────────────────────────────────────────────────────┘
                                   ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 4: VIDEO GEN & DELIVERY                      │
├─────────────────────────────────────────────────────────────────────┤
│  Generate Avatar Video (WaveSpeed InfiniteTalk)                     │
│                                   ↓                                 │
│                     Wait → Poll → Video Complete?                   │
│                                   ↓ (loop until ready)              │
│  Download → Upload to Drive → Update Lead Sheet with Link           │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Apify](https://apify.com) (Lead scraper and LinkedIn enrichment actors)
- [Google AI Studio](https://aistudio.google.com) (for Gemini 3 Pro)
- [WaveSpeed](https://wavespeed.ai) (for ElevenLabs TTS and InfiniteTalk video)
- [Google Sheets](https://sheets.google.com) (lead management)
- [Google Drive](https://drive.google.com) (video storage)

### 2. Import the Workflow

1. Download `Personalized-Video-Prospector.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Lead Scraping

Update the `Config Scraper` node with your criteria:
- Number of leads to scrape
- Job titles (CEO, Sales Director, etc.)
- Seniority levels
- Locations and regions
- Company size and industries
- Salary ranges

### 4. Configure Google Sheets

Create a spreadsheet with columns:
`Name`, `Email`, `Linkedin`, `Industry`, `Job_title`, `Company`, `Job Summary`, `Video-Outreach`, `Status`

### 5. Configure Credentials

1. **Apify**: Connect your account for lead scraping and LinkedIn enrichment
2. **Google Gemini**: Add your API key for script generation
3. **WaveSpeed**: Add your API key for ElevenLabs TTS and video generation
4. **Google Sheets/Drive**: Authorize OAuth2 access

### 6. Upload Your Avatar Image

Upload a headshot to Google Drive and update the image URL in the `Start Video Gen` node.

## The Script Generation Engine

The AI finds unique hooks using this priority:
1. Patents, Publications, or Awards (highest authority)
2. Volunteering experience or causes (high character)
3. Unique hobbies from About section (high personalization)
4. Specific certifications (medium authority)
5. University/Location (fallback)

Scripts include audio tags for emotion:
- `[laughs]`, `[sighs]`, `[excited]`, `[curious]`, `[whispers]`
- Ellipses (...) for pauses
- ALL CAPS for emphasis

## Example Use Cases

- **SDRs**: Scale personalized outreach without recording thousands of videos
- **Agency Owners**: Create custom pitch videos for prospects at scale
- **Recruiters**: Send personalized video messages to candidates
- **Founders**: Build relationships with investors using personal touches

## Pro Tips

- Start with small batches (10-20 leads) to test your script template
- The hook priority ensures every video feels genuinely researched
- WaveSpeed polling loops handle variable render times automatically
- Review a few videos before scaling to ensure quality
- Personalize your avatar image to match your brand
- The script includes a soft CTA - adjust the pitch section for your offer

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Apify, Google Gemini, WaveSpeed (ElevenLabs + InfiniteTalk), and Google Drive
