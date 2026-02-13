# 🎨 AI-Powered Logo & Brand Asset Generator

> Generate a complete brand identity from a simple company description - logos, color palettes, fonts, and realistic mockups.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

AI-Powered Logo & Brand Asset Generator is an automation built in n8n that automatically:

- Accepts a company name and description via web form
- Uses Claude Opus as a "Creative Director" to brainstorm 3 distinct logo concepts (Wordmark, Abstract Symbol, Pictorial Mark)
- Generates high-quality vector-style logos using Google Gemini image generation
- Reverse-engineers a complete brand identity from each logo (color palette, fonts, mood)
- Creates realistic brand asset mockups (business cards, packaging, app screens)
- Stores everything in Airtable as a complete brand package

It's designed for agencies, freelancers, and entrepreneurs who want to rapidly prototype brand identities for client pitches or new ventures.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 🎯 **3 Logo Variations** | Generates Modern Wordmark, Abstract Symbol, and Pictorial Mark concepts automatically |
| 🤖 **Claude Creative Director** | Uses Claude Opus to brainstorm concepts with Swiss-style minimalist design principles |
| 🖼️ **AI Image Generation** | Gemini 3 Pro creates flat vector-style logos from detailed prompts |
| 🔍 **Brand Reverse-Engineering** | Vision AI analyzes logos to extract color palettes (hex codes), font pairings, and mood |
| 📦 **Asset Mockup Generation** | Creates realistic mockups like business cards, packaging, and app screens |
| 🗄️ **Airtable Brand Library** | Stores all assets, prompts, and brand data in one organized database |

## 🏗️ Workflow Architecture

```
Phase 1: Input & Concept Generation
Form Trigger → Claude Opus (Creative Director) → JSON Parser
                         ↓
              3 Logo Concepts (Wordmark, Abstract, Pictorial)

Phase 2: Logo Generation Loop
Loop → Airtable Record → Gemini Image Gen → Upload Logo

Phase 3: Brand Reverse-Engineering
Vision Model (Analyze Logo) → Extract Palette/Fonts/Mood → Save to Airtable

Phase 4: Asset Mockup Production
Loop Asset Ideas → Fetch Logo → Gemini Edit → Upload Mockup → Mark Done
```

The workflow processes each logo concept independently, generating the image, analyzing it for brand elements, then creating realistic mockups before moving to the next concept.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [OpenRouter](https://openrouter.ai) (for Claude Opus access)
- [Google AI Studio](https://aistudio.google.com) (for Gemini image generation and vision)
- [Airtable](https://airtable.com) (for asset storage)

### 2️⃣ Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **OpenRouter**: Add your API key for Claude Opus access
2. **Google Gemini**: Add your API key for Gemini 3 Pro image generation
3. **Airtable**: Create a base called "AI-Powered Logo & Brand Asset Generator" with columns:
   - `Project Name` (text)
   - `Description` (long text)
   - `Status` (single select: To Generate/Generating/Done)
   - `Logo Prompt` (long text)
   - `Logo_Asset` (attachment)
   - `Brand Concept` (long text)
   - `Color Palette` (text)
   - `Suggested Font Pairing` (text)
   - `Asset_Ideas` (attachment)

### 4️⃣ Activate the Form

The workflow uses an n8n form trigger. Once activated, you'll get a URL to submit brand requests.

## 🧪 Example Use Cases

- **Design Agencies**: Rapidly prototype 3 brand directions for client pitches
- **Startup Founders**: Generate a complete brand identity before hiring a designer
- **Freelancers**: Create spec work for prospective clients in minutes
- **Product Teams**: Quickly visualize brand concepts for new product lines

## 💡 Pro Tips

- The Claude prompt enforces "Swiss International Style × contemporary tech branding" - modify it for different aesthetics
- Gemini image generation works best with flat, minimalist designs - adjust prompts for other styles
- Use the Airtable base as a portfolio to show clients your rapid prototyping capability
- The vision model extracts hex codes - copy them directly into design tools
- Asset mockups can be customized by editing the `asset_prompts` in the vision analysis prompt

---

## 🚀 Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[→ Join The Build Room](https://www.skool.com/build-room)

---

Built with ❤️ using n8n, Claude Opus, Google Gemini, and Airtable
