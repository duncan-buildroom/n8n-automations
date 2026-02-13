# 🍌 Nano Banana Showcase

> Five powerful AI image generation use cases powered by Gemini 3 Pro Image Preview.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Nano Banana Showcase demonstrates five practical AI image generation workflows built in n8n, all powered by Google Gemini 3 Pro Image Preview:

1. **Brand Review Generator** - Transform customer reviews into luxury social media graphics
2. **SaaS Wrapped Generator** - Create "Spotify Wrapped" style year-in-review infographics
3. **Real Estate AI Renovator** - Virtually renovate rooms in any design style
4. **Billboard Localizer** - Translate and replace billboard text while preserving perspective
5. **Napkin Sketch to UI Prototype** - Convert hand-drawn sketches into high-fidelity UI mockups

Each workflow pulls data from Google Sheets, generates images via AI, uploads to Google Drive, and updates status.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Use Case | Description |
|----------|-------------|
| 🌟 **Review Graphics** | Generates Instagram-ready review cards with star ratings, brand colors, and logo |
| 📊 **SaaS Wrapped** | Creates vibrant year-in-review infographics with user stats and archetypes |
| 🏠 **Room Renovation** | Transforms old room photos into photorealistic renovated spaces |
| 🌍 **Billboard Localization** | Replaces text on signs/billboards while matching font, perspective, and lighting |
| 📱 **UI Prototyping** | Converts napkin sketches into Figma-quality interface mockups |

## Workflow Architecture

```
Manual Trigger
      ↓
      ├──→ Get Review Data ──→ Fetch Logo ──→ Generate Review Graphic ──→ Upload ──→ Update Status
      │
      ├──→ Get User Stats ──→ Fetch Logo ──→ Generate SaaS Wrapped ──→ Upload ──→ Update Status
      │
      ├──→ Get Room Data ──→ Fetch Image ──→ Renovate Room AI ──→ Upload ──→ Update Status
      │
      ├──→ Get Billboard Data ──→ Fetch Image ──→ Localize Text ──→ Upload ──→ Update Status
      │
      └──→ Get Sketch Data ──→ Fetch Image ──→ Generate UI ──→ Upload ──→ Update Status
```

All five workflows run in parallel, processing any items with "ready" status in their respective sheets.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Google AI Studio](https://aistudio.google.com) (for Gemini 3 Pro Image Preview access)
- [Google Sheets](https://sheets.google.com) (for data management)
- [Google Drive](https://drive.google.com) (for image storage)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Google Sheets

Create a spreadsheet with these sheets:

**reviews**: `id`, `reviewer_name`, `rating`, `review_text`, `date`, `status`, `Img URI`

**userstats**: `id`, `user_name`, `year`, `total_runs`, `ghost_shift_hours`, `hours_saved`, `archetype`, `status`, `Img URI`

**rooms**: `id`, `property_address`, `room_type`, `desired_renovation_style`, `before_image_url`, `status`, `after_image_url`

**billboard**: `id`, `master_image_url`, `original_text`, `translated_text`, `target_region`, `status`, `image_URI`

**napkin drawing**: `id`, `project_name`, `sketch_image_url`, `ui_style`, `status`, `image_Uri`

### 4. Configure Credentials

1. **Google Gemini**: Add your API key for Gemini 3 Pro Image Preview
2. **Google Sheets**: Authorize OAuth2 and update the document ID
3. **Google Drive**: Authorize OAuth2 and set folder IDs for each output type

### 5. Add Your Logo

Upload your brand logo to Google Drive and update the logo URL in the workflow for review and wrapped generators.

## Use Case Details

### 1. Brand Review Generator
- Creates 1080x1080 Instagram review graphics
- Extracts brand colors from your logo
- Renders star ratings dynamically
- Perfect for testimonial marketing

### 2. SaaS Wrapped Generator
- Creates 1080x1920 vertical infographics
- "Spotify Wrapped" aesthetic with neon gradients
- Displays automation stats, hours saved, and user archetype
- Great for year-end customer engagement

### 3. Real Estate AI Renovator
- Maintains room structure and perspective
- Applies specified design styles (Modern Scandinavian, etc.)
- Photorealistic output for listings
- Helps buyers visualize potential

### 4. Billboard Localizer
- Identifies and extracts text from images
- Replaces with translated text
- Matches font, color, perspective, and lighting
- Essential for global marketing campaigns

### 5. Napkin Sketch to UI
- Interprets hand-drawn wireframes
- Applies professional design systems
- Outputs Stripe/Linear quality mockups
- Accelerates product ideation

## Pro Tips

- Set status to "ready" in Google Sheets to queue items for processing
- Upload high-quality source images for best AI results
- The renovation AI works best with clear, well-lit room photos
- Billboard localization handles perspective-skewed signs automatically
- UI prototypes follow 8px grid systems for production-ready outputs

---

## Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[Join The Build Room](https://www.skool.com/build-room)

---

Built with n8n, Google Gemini 3 Pro Image Preview, Google Sheets, and Google Drive
