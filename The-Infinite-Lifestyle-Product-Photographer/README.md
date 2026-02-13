# 📸 The "Infinite Lifestyle" Product Photographer

> Transform a single product image into 8 professional lifestyle photographs across diverse settings.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Infinite Lifestyle Product Photographer is an n8n automation that automatically:

- Accepts a product image and campaign context
- Analyzes the product using Gemini AI to understand its visual characteristics
- Generates 8 diverse lifestyle scene descriptions (location, mood, lighting, weather)
- Places the product into each scene while maintaining product integrity
- Creates professional 8K commercial-quality photographs
- Organizes all images in a dedicated Google Drive folder

It's designed for ecommerce brands, product marketers, and content creators who need diverse product photography without expensive photoshoots.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🖼️ **Product Analysis** | Gemini extracts visual details from your product image |
| 🌍 **8 Diverse Scenes** | Generates varied locations, times, and demographics |
| 🎨 **Lifestyle Integration** | Places product naturally into realistic environments |
| ✨ **8K Quality** | Commercial-grade, high-detail output images |
| 📁 **Auto-Organized** | Creates project folders in Google Drive |
| 🔄 **Batch Processing** | All 8 scenes generated in one workflow run |

## Scene Generation Details

Each scene includes:
- **Location**: Urban park, coastal boardwalk, downtown café, etc.
- **Description**: Activity or interaction in the scene
- **Time of Day**: Morning, afternoon, evening, or night
- **Demographics**: Target audience visible in scene
- **Mood**: Energetic, relaxed, professional, casual
- **Weather**: Sunny, overcast, or contextually appropriate

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 1: INPUT & ANALYSIS                        │
├─────────────────────────────────────────────────────────────────────┤
│  Form Trigger:                                                      │
│  • Product Name                                                     │
│  • Product Image (.jpg, .png)                                       │
│  • Product & Campaign Description                                   │
│                              ↓                                      │
│  ┌────────────────────┐    ┌────────────────────┐                  │
│  │ Generate Scene     │    │ Create Drive       │                  │
│  │ Prompts (Gemini)   │    │ Folder             │                  │
│  └────────────────────┘    └────────────────────┘                  │
│  • Analyzes product                                                 │
│  • Creates 8 scene descriptions                                     │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 2: DATA PREPARATION                        │
├─────────────────────────────────────────────────────────────────────┤
│  Extract Image Binary → Format Scene Output                         │
│                              ↓                                      │
│  Merge Image & Scenes → Split Scenes (8 items)                      │
│                              ↓                                      │
│           Set Image Binary → Prepare for Generation                 │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 3: GENERATION & STORAGE                      │
├─────────────────────────────────────────────────────────────────────┤
│  For Each Scene:                                                    │
│  Generate Lifestyle Image (Gemini 3 Pro Image Preview)              │
│  • Maintains exact product appearance                               │
│  • Matches lighting/shadows to scene                                │
│  • Places product as focal point                                    │
│  • Creates 8K commercial-quality output                             │
│                              ↓                                      │
│              Upload Result to Drive (per scene)                     │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Google AI Studio](https://makersuite.google.com) (Gemini 3 Pro + Gemini 3 Pro Image Preview)
- [Google Drive](https://drive.google.com) (image storage)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Set Up Google Drive

1. Create a parent folder for product photography projects
2. Update the folder ID in "Create Drive Folder" node

### 4. Configure Credentials

1. **Google Gemini**: Add your API key for analysis and image generation
2. **Google Drive**: Authorize OAuth2 for file uploads

## Example Use Cases

- **eCommerce Brands**: Generate product shots for different seasons and contexts
- **Amazon Sellers**: Create lifestyle images for A+ content
- **Marketing Agencies**: Scale product photography for multiple clients
- **Social Media Managers**: Generate diverse content from a single product shot

## Pro Tips

- Higher quality input images produce better lifestyle outputs
- Be specific in your campaign description for more relevant scenes
- The AI maintains product logos and details - no distortion
- Scene lighting automatically matches the environment
- Each scene is named by location for easy organization
- Run multiple times with different descriptions for even more variety

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Google Gemini 3 Pro, Gemini 3 Pro Image Preview, and Google Drive
