# 🎨 Slide Designer

> Transform any topic into a professionally designed presentation deck with AI-generated visual slides.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Slide Designer is an AI-powered automation built in n8n that automatically:

- Accepts presentation topics via a web form
- Uses Perplexity Sonar Reasoning Pro to research and structure content
- Defines a cohesive visual theme (colors, typography, mood)
- Drafts 6-10 minimalist slides with one key message each
- Generates complete visual slides using Gemini 3 Pro Image Preview
- Compiles all slides into a downloadable PDF
- Redirects users directly to their finished deck

It's designed for professionals who need polished presentation decks without spending hours in design tools.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔍 **Research-Backed** | Perplexity Reasoner finds current data and statistics for your topic |
| 🎨 **Visual Theming** | AI defines color palette, typography, and mood for consistency |
| 📝 **Minimalist Content** | Each slide has one key message - maximum impact, minimum clutter |
| 🖼️ **Full Slide Generation** | Gemini creates complete slides with text, graphics, and layout |
| 📄 **PDF Compilation** | PDF.co merges all slides into a single downloadable deck |
| 🔗 **Instant Delivery** | Users are redirected to Google Drive download link |

## Workflow Architecture

```
Form Trigger (Topic & Context)
              ↓
   Generate Slide Content (Perplexity Sonar Reasoning Pro)
   • Research topic
   • Define visual theme
   • Draft 6-10 slides
              ↓
        Format as JSON (GPT-4 Mini)
              ↓
        Loop Through Slides
              ↓
   ┌──────────┴──────────┐
   ↓                     ↓
Slide 1              Slide 2...
   ↓                     ↓
   Gemini: Visual Slide Creator (Generate full slide image)
   ↓                     ↓
   Save to Google Drive (Temp)
   └──────────┬──────────┘
              ↓
       Collect All Image Links
              ↓
      PDF.co (Images to PDF)
              ↓
       Wait → Poll Status → Check Complete?
                    ↓ (loop until ready)
       Download PDF → Save to Drive
              ↓
       Redirect User to Download
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [OpenRouter](https://openrouter.ai) (for Perplexity Sonar Reasoning Pro)
- [OpenAI](https://platform.openai.com) (for GPT-4 Mini parser)
- [Google AI Studio](https://aistudio.google.com) (for Gemini 3 Pro Image Preview)
- [PDF.co](https://pdf.co) (for PDF compilation)
- [Google Drive](https://drive.google.com) (for storage and delivery)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **OpenRouter**: Add your API key for Perplexity Sonar Reasoning Pro
2. **OpenAI**: Add your API key for GPT-4 Mini
3. **Google Gemini**: Add your API key for image generation
4. **PDF.co**: Add your API key as HTTP Header Auth
5. **Google Drive**: Authorize OAuth2 and set your folders

### 4. Deploy the Form

1. Activate the workflow to generate the form URL
2. Share the URL or embed it in your tools
3. Users enter their topic and receive a download link when complete

## Slide Design Principles

The AI follows strict minimalist rules:
- **Maximum 3 bullet points per slide** (prefer 1-2)
- **Maximum 10 words per bullet point**
- **One key message per slide**
- **Headlines: 5-8 words maximum**
- **More content = more slides**, not longer slides

## Slide Structure Template

1. **Title Slide** - Bold headline only
2. **Problem** - One sentence + striking visual
3. **Key Insight 1** - One data point + source
4. **Key Insight 2** - One data point + source
5. **Key Insight 3** - One data point + source
6. **Solution** - One clear benefit
7. **Impact** - One powerful statistic
8. **Conclusion** - One memorable call to action

## Example Use Cases

- **Sales Teams**: Generate pitch decks from product briefs
- **Consultants**: Create client presentation decks quickly
- **Educators**: Design lecture slides from topic outlines
- **Startups**: Build investor decks without a designer

## Pro Tips

- Provide context in your topic submission for better results
- The visual theme is consistent across all slides automatically
- Gemini generates complete slides with text and graphics included
- PDF.co runs asynchronously - polling handles variable render times
- Each slide image is saved to Drive for individual access too

---

## Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[Join The Build Room](https://www.skool.com/build-room)

---

Built with n8n, Perplexity Sonar, Google Gemini, PDF.co, and Google Drive
