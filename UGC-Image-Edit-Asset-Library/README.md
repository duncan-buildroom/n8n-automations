# 🎨 UGC Image Edit & Asset Library

> Transform a single UGC asset into multiple brand-consistent marketing variants with automated logo integration.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The UGC Image Edit & Asset Library is an n8n automation that automatically:

- Receives UGC asset records from Airtable via webhook
- Analyzes the original asset and brand logo using GPT-4o
- Generates multiple production-ready editing prompts
- Creates diverse variants with unique angles, lighting, and compositions
- Integrates brand logos intelligently (watermark or environmental)
- Saves all variants back to Airtable with tags for organization

It's designed for ecommerce brands and agencies who need to scale UGC content while maintaining brand consistency.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔗 **Airtable Integration** | Receives records and stores variants automatically |
| 🏷️ **Brand Config** | Pulls logo and brand context from configuration table |
| 🖼️ **Asset Analysis** | GPT-4o understands the original subject and clothing |
| ✍️ **Smart Prompts** | Generates production-ready editing instructions |
| 📐 **Diverse Angles** | Each variant uses unique camera perspective |
| 💡 **Varied Lighting** | Different lighting styles per variant |
| 🏷️ **Logo Rules** | Intelligent placement (watermark or environmental) |
| 🏷️ **Auto-Tagging** | Variants saved with searchable tags |

## Variant Generation Rules

### Subject Preservation (Non-Negotiable)
- Identical body shape, face, identity
- Identical clothing, graphics, textures, colors
- Identical text on clothing or packaging
- Subject is always the focal point

### Required Camera Angles
- Dramatic Low-Angle Close-Up
- Wide-Angle Environmental Shot
- High-Key Aerial / Flat-Lay
- Tight Crop Macro Detail Shot

### Lighting Styles
- Cinematic rim lighting
- High-key soft diffused
- Moody directional lighting
- Natural golden-hour sunlight
- Neon or ambient colored lighting

### Logo Integration
- One logo per image only
- Never on subject, clothing, or product surface
- High contrast vs placement
- One variant: environmental integration
- All others: corner watermark

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                       PHASE 1: RECEIVE                              │
├─────────────────────────────────────────────────────────────────────┤
│  Webhook: Receive UGC Record ID                                     │
│                    ↓                                                │
│  Airtable: Get UGC Asset Record                                     │
│  • Asset image URL                                                  │
│  • Variants quantity                                                │
│  • Context description                                              │
│                    ↓                                                │
│  Airtable: Get Brand Configuration                                  │
│  • Logo image                                                       │
│  • Brand context                                                    │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                      PHASE 2: ANALYZE                               │
├─────────────────────────────────────────────────────────────────────┤
│  GPT-4o: Get Logo Description                                       │
│  • Brand name/text visible                                          │
│  • Primary colors                                                   │
│  • Key visual elements                                              │
│  • Design style                                                     │
│                    ↓                                                │
│  GPT-4o: Generate Editing Prompts                                   │
│  • Analyzes original asset                                          │
│  • Creates N distinct prompts                                       │
│  • Applies angle, lighting, logo rules                              │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                     PHASE 3: GENERATE                               │
├─────────────────────────────────────────────────────────────────────┤
│  Split: Prompts for Iteration                                       │
│                    ↓                                                │
│  For Each Prompt:                                                   │
│  Kie AI: Generate Image Variant                                     │
│  → Wait → Check Status → Loop until complete                        │
│                    ↓                                                │
│  Airtable: Create Asset Record                                      │
│  • image_url                                                        │
│  • linked to UGC Asset                                              │
│  • linked to brand                                                  │
│  • tags for organization                                            │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [OpenAI](https://platform.openai.com) (GPT-4o for analysis and prompts)
- [Kie AI](https://kie.ai) (image generation)
- [Airtable](https://airtable.com) (asset management)

### 2. Import the Workflow

1. Download `UGC-Image-Edit-Asset-Library.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Airtable

Create a base with these tables:
- **UGC Assets**: Name, Asset (attachment), Context, Variants Qty, Configuration (link)
- **Brand Configuration**: Logo (attachment), brand context
- **Assets**: image_url, asset (attachment), tags, UGC Asset (link), brand (link)

### 4. Configure Credentials

1. **OpenAI**: Add your API key for GPT-4o
2. **Kie AI**: Add your API key for image generation
3. **Airtable**: Authorize OAuth2 and update base/table IDs

## Example Tags

- wristwatch, fashion accessory, street style
- outdoor, lifestyle, ecommerce
- brand promotion, modern style, casual wear
- t-shirt, branding, indoor lifestyle
- menswear, logo apparel, UGC

## Pro Tips

- Higher variants quantity = more diverse content library
- Brand context influences scene style and aesthetic
- Each variant gets a unique angle - no repeats
- Logo environmental integration only happens once per batch
- The system preserves exact clothing and product details
- Use tags to filter assets for specific campaigns
- Trigger via webhook when new UGC is uploaded to Airtable

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, OpenAI GPT-4o, Kie AI, and Airtable
