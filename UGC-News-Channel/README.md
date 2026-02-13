# 📺 UGC News Channel

> Automated AI news anchor that creates daily talking-head videos from RSS feeds.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The UGC News Channel is an n8n automation that automatically:

- Triggers daily at a scheduled time (7 AM)
- Pulls the latest news from multiple RSS feeds
- Generates a news script using AI
- Creates a consistent AI anchor image with Kie AI
- Converts the script to speech using WaveSpeed
- Produces a talking-head video with InfiniteTalk
- Delivers ready-to-publish news content

It's designed for content creators who want to run automated news channels without appearing on camera.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| ⏰ **Scheduled Trigger** | Runs automatically every morning |
| 📡 **Multi-Source RSS** | Pulls from Thomson Reuters, TechCrunch, CNN |
| ✍️ **AI Script Writer** | Generates news scripts from aggregated content |
| 🎭 **Anchor Persona** | Configurable mood and presentation style |
| 🖼️ **AI Anchor Image** | Consistent character generation via Kie AI |
| 🎙️ **Text-to-Speech** | Natural voice via WaveSpeed |
| 🎬 **Talking Head Video** | InfiniteTalk creates lip-synced videos |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                       PHASE 1: TRIGGER                              │
├─────────────────────────────────────────────────────────────────────┤
│  Daily Morning Trigger (7 AM)                                       │
│                    ↓                                                │
│  ┌────────────────┐ ┌────────────────┐ ┌────────────────┐          │
│  │ Thomson Reuters│ │  TechCrunch    │ │    CNN         │          │
│  │    RSS Feed    │ │   RSS Feed     │ │  RSS Feed      │          │
│  └────────────────┘ └────────────────┘ └────────────────┘          │
│           └──────────────────┴──────────────────┘                   │
│                              ↓                                      │
│                    Aggregate News Items                             │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                     PHASE 2: SCRIPT                                 │
├─────────────────────────────────────────────────────────────────────┤
│  AI Script Writer                                                   │
│  • Processes aggregated news                                        │
│  • Generates broadcast-ready script                                 │
│  • Formats for TTS delivery                                         │
│                    ↓                                                │
│  Anchor Persona Config                                              │
│  • Sets mood and presentation style                                 │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                PHASE 3: PARALLEL GENERATION                         │
├─────────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┐    ┌─────────────────────────┐        │
│  │   Kie AI: Generate      │    │  WaveSpeed: Generate    │        │
│  │   Anchor Image          │    │  TTS Audio              │        │
│  │                         │    │                         │        │
│  │   → Wait 10s            │    │   → Wait 15s            │        │
│  │   → Check Status        │    │   → Check Status        │        │
│  │   → Loop if needed      │    │   → Loop if needed      │        │
│  │   → Set Image URL       │    │   → Set Audio URL       │        │
│  └─────────────────────────┘    └─────────────────────────┘        │
│                    └──────────────────┘                             │
│                              ↓                                      │
│                   Combine Audio & Image                             │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                   PHASE 4: VIDEO PRODUCTION                         │
├─────────────────────────────────────────────────────────────────────┤
│  WaveSpeed InfiniteTalk: Create Video                               │
│  • Audio URL                                                        │
│  • Image URL                                                        │
│  • Mood prompt from persona config                                  │
│  • Script context                                                   │
│  • 480p resolution                                                  │
│                    ↓                                                │
│  Wait for Video → Check Status → Loop if needed                     │
│                    ↓                                                │
│             Final Video Ready for Publishing                        │
└─────────────────────────────────────────────────────────────────────┘
```

## News Sources

| Source | Content Type |
|--------|-------------|
| **Thomson Reuters** | Financial and business news |
| **TechCrunch** | Technology and startup news |
| **CNN** | Top stories and breaking news |

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Kie AI](https://kie.ai) (anchor image generation)
- [WaveSpeed](https://wavespeed.ai) (TTS and InfiniteTalk video)

### 2. Import the Workflow

1. Download `UGC-News-Channel.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure the Schedule

1. Update the trigger time in "Daily Morning Trigger"
2. Default is 7 AM daily

### 4. Customize RSS Feeds

1. Add or remove RSS feed nodes as needed
2. Update URLs to your preferred news sources

### 5. Configure Credentials

1. **Kie AI**: Add your API key for image generation
2. **WaveSpeed**: Add your API key for TTS and video

### 6. Set Anchor Persona

Configure the mood and style for your AI anchor in the "Anchor Persona Config" node.

## Example Use Cases

- **News Channels**: Automated daily news updates
- **Industry Updates**: Niche-specific news summaries
- **Brand Channels**: Curated news relevant to your audience
- **Content Creators**: Faceless news content at scale

## Pro Tips

- Customize RSS feeds to match your niche
- The anchor persona mood affects facial expressions and delivery
- InfiniteTalk creates natural lip-sync from the audio
- Script context helps the video generation match the content tone
- Run at consistent times to build audience habits
- Add more RSS sources for comprehensive coverage
- Consider running multiple times daily for breaking news channels

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Kie AI, WaveSpeed (TTS + InfiniteTalk), and RSS Feeds
