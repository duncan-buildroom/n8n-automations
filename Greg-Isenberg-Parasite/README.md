# 🐦 Greg Isenberg Parasite

> Turn viral Twitter/X threads into brand-aligned content with AI-powered text remixing and image regeneration.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Greg Isenberg Parasite is an AI-powered automation built in n8n that automatically:

- Scrapes any Twitter/X post via RapidAPI including text and images
- Rewrites the post copy in your brand voice using Gemini 3 Pro
- Analyzes the original image and generates a brand-styled prompt
- Creates a new image matching your aesthetic via Kie.ai
- Posts the remixed content to your Twitter/X account via Blotato

It's designed for content creators who want to ethically repurpose viral content trends while maintaining their unique brand identity.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔗 **Tweet Scraping** | Extracts full tweet content including extended text and media via RapidAPI |
| ✍️ **Voice Remixing** | Gemini 3 Pro rewrites posts in your brand's tone, strategy, and style |
| 🎨 **Image Analysis** | AI analyzes original images and creates detailed regeneration prompts |
| 🖼️ **Brand-Styled Images** | Kie.ai generates new images in your cyberpunk-minimal aesthetic |
| ⏱️ **Smart Polling** | Automatic retry loop waits for image generation to complete |
| 📤 **Auto-Publishing** | Blotato posts the final remixed content to Twitter/X |

## Workflow Architecture

```
Form Submission (Tweet URL) → Scrape Tweet via RapidAPI
                                      ↓
              ┌───────────────────────┴───────────────────────┐
              ↓                                               ↓
    Remix Post (Gemini 3 Pro)                    Analyze Image (Gemini 3 Pro)
              ↓                                               ↓
              │                                     Create Image (Kie.ai)
              │                                               ↓
              │                                    Wait → Poll → Check Status
              │                                               ↓ (loop until ready)
              └───────────────────────┬───────────────────────┘
                                      ↓
                                    Merge
                                      ↓
                            Post to Twitter/X (Blotato)
```

The workflow uses parallel processing to remix text and regenerate images simultaneously, then merges results for final publishing.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [RapidAPI](https://rapidapi.com) (Twitter scraping API - twitter241)
- [Google AI Studio](https://aistudio.google.com) (for Gemini 3 Pro access)
- [Kie.ai](https://kie.ai) (for image generation)
- [Blotato](https://blotato.com) (for Twitter/X posting)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **RapidAPI**: Subscribe to the Twitter241 API and add your API key as HTTP Header Auth
2. **Google Gemini**: Add your API key for Gemini 3 Pro access
3. **Kie.ai**: Get your API key from Kie.ai dashboard and add as HTTP Header Auth
4. **Blotato**: Connect your Twitter/X account and update the account ID in the posting node

### 4. Customize Your Brand Voice

Edit the `Remix Post - Gemini 3 Pro` node system prompt to match your brand:
- Update the tone guidelines
- Modify the target audience description
- Adjust the content themes and keywords

### 5. Customize Your Visual Aesthetic

Edit the `Analyze Image - Gemini 3 Pro` node prompt to match your brand aesthetic:
- Update the color palette (default: white, black, yellow)
- Modify the style direction (default: cyberpunk-minimal)
- Adjust the visual motifs and themes

## Example Use Cases

- **Thought Leaders**: Remix viral business insights in your unique voice
- **Agency Owners**: Create on-brand content from trending industry posts
- **Content Creators**: Transform popular threads into your signature style
- **Personal Brands**: Stay relevant by adding your perspective to viral moments

## Pro Tips

- Use the form trigger to manually curate which posts to remix for quality control
- The brand voice prompt is highly detailed - customize it thoroughly for best results
- Kie.ai's nano-banana-pro model excels at illustrated, stylized imagery
- Add more posting destinations (Instagram, LinkedIn) by duplicating the Blotato node
- Consider adding a human review step before auto-posting for sensitive topics

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Google Gemini 3 Pro, Kie.ai, and Blotato
