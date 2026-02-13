# 🎯 Digital Ad A/B Tester

> Generate multiple ad creative variations from a single product image - different angles, headlines, and visual hooks for Facebook/Instagram A/B testing.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

Digital Ad A/B Tester is an AI-powered automation built in n8n that automatically:

- Accepts a product image, target personas, and selling points via web form
- Uses Gemini Vision to analyze the product and identify hardware details for preservation
- Generates 1-8 distinct ad creative concepts with different strategy angles
- Creates headlines tailored to each target persona
- Renders final ad images using AI image editing (preserving product pixels exactly)
- Integrates headline text as native overlays
- Saves all variations to Google Drive organized by campaign

It's designed for performance marketers, e-commerce brands, and agencies who need multiple ad variations for A/B testing without hiring a design team.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 🔍 **Product Preservation** | AI analyzes and protects exact product details (cameras, bezels, etc.) during editing |
| 🎭 **Persona-Based Headlines** | Generates different headlines for each target audience |
| 🎨 **4 Strategy Angles** | Benefit Visualization, Social Proof, Lifestyle Aspirational, and Pattern Interrupt |
| 🖼️ **AI Background Editing** | Gemini edits backgrounds and adds graphic elements while preserving product |
| 📝 **Native Text Integration** | Headlines rendered directly into the image as professional overlays |
| 📁 **Campaign Organization** | Auto-creates Google Drive folders per product/audience |

## 🏗️ Workflow Architecture

```
Form Trigger (Product Image + Details)
        ↓
┌───────┼───────────┐
↓       ↓           ↓
GDrive  Extract    Gemini Vision
Folder  Image      (Analyze + Concept)
        ↓
    Merge All Data
        ↓
    Loop: For Each Variation
        ↓
    Gemini Edit (Background + Headlines)
        ↓
    Save to Google Drive
```

The workflow analyzes the product, generates strategic ad concepts, then renders each variation while preserving the original product pixels.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [Google AI Studio](https://aistudio.google.com) (for Gemini Vision and image editing)
- [Google Drive](https://drive.google.com) (for asset storage)

### 2️⃣ Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **Google Gemini**: Add your API key for vision analysis and image editing
2. **Google Drive**: Authorize OAuth2 and create a folder "Social Media - Ads"

### 4️⃣ Update Folder ID

In the "Drive: Create Campaign Folder" node, update the parent folder ID to your "Social Media - Ads" folder.

## 🧪 Example Use Cases

- **E-commerce Brands**: Generate 8 ad variations from one product photo for Facebook testing
- **Agencies**: Rapidly produce client ad concepts without design resources
- **DTC Startups**: Test different value propositions across audience segments
- **Performance Marketers**: Create visual A/B tests at scale

## 💡 Pro Tips

- The "Product Preservation" system explicitly describes hardware details (e.g., "3 camera lenses") to prevent AI hallucination
- Use descriptive persona names (e.g., "Busy Moms," "Tech Geeks") for better headline targeting
- The 4 strategy angles map to proven ad psychology frameworks
- Start with 4-8 variations to test, then double down on winners
- Each variation gets its own strategy angle - great for identifying what resonates

---

## 🚀 Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[→ Join The Build Room](https://www.skool.com/build-room)

---

Built with ❤️ using n8n, Google Gemini, and Google Drive
