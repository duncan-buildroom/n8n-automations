# 📊 The "Case Study" Engine

> Transform raw success stories into polished 8-slide LinkedIn carousels using the PAS (Problem-Agitation-Solution) framework.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Case Study Engine is an n8n automation that automatically:

- Takes raw notes, bullet points, or transcripts from client success stories
- Structures content into 8 slides using the proven PAS framework
- Generates a branded abstract background template preserving your logo
- Renders each slide with AI-generated text and relevant visuals
- Uploads the complete carousel to Google Drive ready for LinkedIn

It's designed for consultants, agencies, and founders who want to turn client wins into high-converting social proof content.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 📝 **Raw Input Intake** | Paste unformatted notes, transcripts, or bullet points |
| 🎯 **PAS Framework** | AI structures content into Problem → Agitation → Solution |
| 🎨 **Brand Templates** | Generates abstract backgrounds with your logo protected |
| 🖼️ **Visual Slides** | Each slide gets fresh icons and graphics relevant to content |
| ✍️ **Style Matching** | Choose Professional, Punchy, or Story-Driven tone |
| 📁 **Auto-Organized** | Creates dated project folders in Google Drive |

## The 8-Slide Structure

| Slide | Purpose | Framework |
|-------|---------|-----------|
| 1 | **The Hook** | Cover slide featuring the key result metric |
| 2 | **The Problem** | Core struggle that makes audience feel seen |
| 3 | **The Agitation** | Financial or emotional cost of not solving |
| 4 | **The Shift** | The turning point - "We realized X was wrong" |
| 5 | **Solution Step 1** | First major action taken |
| 6 | **Solution Step 2** | Second major action or insight |
| 7 | **The Results** | Hard numbers and the "happy ending" |
| 8 | **CTA** | Strong call to action for target audience |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                     PHASE 1: INPUT & SETUP                          │
├─────────────────────────────────────────────────────────────────────┤
│  Form Trigger: Intake Case Study                                    │
│  • Raw Success Story / Notes                                        │
│  • Key Result (Hook Metric)                                         │
│  • Target Audience                                                  │
│  • Writing Style                                                    │
│                              ↓                                      │
│  ┌────────────────┐  ┌────────────────┐  ┌────────────────┐        │
│  │ Set Logo URL   │  │ Generate Copy  │  │ Create Folder  │        │
│  │ → Fetch Logo   │  │ (Gemini)       │  │ (Google Drive) │        │
│  └────────────────┘  └────────────────┘  └────────────────┘        │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                   PHASE 2: ASSET GENERATION                         │
├─────────────────────────────────────────────────────────────────────┤
│  AI: Generate Slide Copy (JSON)     AI: Create Background Template  │
│  • 8 slides with titles/body        • Abstract fluid shapes         │
│  • Max 8 words per title            • Logo preserved in corner      │
│  • Max 25 words per body            • Clean center for text         │
│  • PAS framework structure          • Matches logo color palette    │
│                    └──────────────────────────┘                     │
│                              ↓                                      │
│                    Merge: Combine Assets                            │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                   PHASE 3: PRODUCTION LOOP                          │
├─────────────────────────────────────────────────────────────────────┤
│  Loop: Split Slides → For Each Slide:                               │
│                              ↓                                      │
│  AI: Render Final Image (Gemini Image Edit)                         │
│  • Preserves logo and background style                              │
│  • Adds new headline and body text                                  │
│  • Generates fresh icons/graphics                                   │
│  • Shows progress indicator (X of 8)                                │
│                              ↓                                      │
│           Drive: Upload Slide → Complete Carousel                   │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Google AI Studio](https://makersuite.google.com) (Gemini 3 Pro + Gemini 3 Pro Image Preview)
- [Google Drive](https://drive.google.com) (carousel storage)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Your Brand Logo

1. Host your logo image at a public URL
2. Update the "Config: Set Logo URL" node with your logo URL
3. The logo will be automatically preserved in all slide designs

### 4. Set Up Google Drive

1. Create a parent folder for all carousels (e.g., "Case Study Carousels")
2. Update the folder ID in "Drive: Create Project Folder" node
3. Each project gets its own dated subfolder

### 5. Configure Credentials

1. **Google Gemini**: Add your API key for text and image generation
2. **Google Drive**: Authorize OAuth2 for file uploads

## Writing Style Options

| Style | Best For | Characteristics |
|-------|----------|-----------------|
| **Professional & Data-Driven** | B2B, enterprise audiences | Numbers-focused, objective, credibility-building |
| **Punchy & Bold** | Social media, attention economy | Short sentences, strong verbs, scroll-stopping |
| **Story-Driven & Emotional** | Consumer brands, personal development | Narrative arc, emotional hooks, relatable |

## Example Use Cases

- **Agency Owners**: Turn client results into lead magnets
- **SaaS Companies**: Showcase customer success stories
- **Consultants**: Build portfolio of transformation stories
- **Coaches**: Share client breakthroughs as social proof

## Pro Tips

- Include a specific number in your "Key Result" - percentages and dollar amounts perform best
- The more detail in your raw notes, the better the AI can find compelling angles
- Target audience affects language calibration - "Engineers" gets technical agitation, "CEOs" gets financial
- Each slide is designed with 80% clean center area for maximum text readability
- The AI generates fresh visuals per slide, not generic stock graphics
- Review and tweak the JSON output before rendering if you want to adjust copy

---

## Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[Join The Build Room](https://www.skool.com/build-room)

---

Built with n8n, Google Gemini 3 Pro, Gemini 3 Pro Image Preview, and Google Drive
