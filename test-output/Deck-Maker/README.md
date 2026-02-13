# 📊 Deck Maker

> Generate a complete, professional presentation deck from a single topic - slides designed, rendered, and compiled to PDF automatically.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

Deck Maker is an AI-powered automation built in n8n that automatically:

- Accepts a presentation topic via web form
- Uses Perplexity AI to research the topic and structure 6-10 minimalist slides
- Defines a visual theme (color palette, typography, visual mood)
- Generates high-fidelity slide images using Gemini image generation
- Compiles all slides into a single PDF using PDF.co
- Saves the finished deck to Google Drive
- Redirects the user directly to the download link

It's designed for busy professionals, consultants, and content creators who need polished presentations without spending hours in PowerPoint.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 🧠 **AI Research & Structure** | Perplexity researches your topic and creates a logical slide flow |
| 🎨 **Visual Theme Generation** | Defines color palette, typography, and mood for consistent design |
| 🖼️ **Gemini Slide Rendering** | Creates professional 16:9 slide images with text and visuals baked in |
| 📄 **Automatic PDF Compilation** | PDF.co merges all slide images into a single downloadable deck |
| ☁️ **Cloud Storage** | Finished decks saved to Google Drive for easy access |
| 🔗 **Direct Download** | User redirected to download link when complete |

## 🏗️ Workflow Architecture

```
Form Trigger (Topic)
        ↓
Perplexity AI (Research + Structure)
        ↓
JSON Parser (Slide Content)
        ↓
Loop: For Each Slide
    ↓
    Gemini (Generate Slide Image)
    ↓
    Save to Google Drive (Temp)
        ↓
Collect All Image Links
        ↓
PDF.co (Images → PDF)
        ↓
Wait → Check Status → Retry if needed
        ↓
Download PDF → Save to Drive → Redirect User
```

The workflow generates content, renders each slide visually, compiles to PDF, then delivers the finished deck.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [OpenRouter](https://openrouter.ai) (for Perplexity AI access)
- [OpenAI](https://platform.openai.com) (for GPT JSON parsing)
- [Google AI Studio](https://aistudio.google.com) (for Gemini image generation)
- [Google Drive](https://drive.google.com) (for file storage)
- [PDF.co](https://pdf.co) (for PDF compilation)

### 2️⃣ Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **OpenRouter**: Add your API key for Perplexity access
2. **OpenAI**: Add your API key for GPT-4 parsing
3. **Google Gemini**: Add your API key for image generation
4. **Google Drive**: Authorize OAuth2 and create two folders:
   - "Deck Maker" (for temporary slide images)
   - "Finished Decks" (for final PDFs)
5. **PDF.co**: Add your API key as HTTP Header Auth

### 4️⃣ Update Folder IDs

Update the Google Drive folder IDs in:
- "Google Drive: Save Temp Images" node
- "Google Drive: Save PDF" node

## 🧪 Example Use Cases

- **Consultants**: Generate client presentation drafts in minutes
- **Sales Teams**: Create quick pitch decks for prospects
- **Educators**: Build lecture slides from topic outlines
- **Marketers**: Produce campaign presentations without design resources

## 💡 Pro Tips

- The slide structure (6-10 slides) follows best practices: hook, problem, insights, solution, impact, CTA
- Adjust the slide count in the content generation prompt for longer or shorter decks
- Perplexity's research capabilities mean your slides include real data and sources
- The visual theme is defined once and applied consistently across all slides
- Use the temp images folder to preview individual slides before PDF compilation

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, Perplexity AI, Google Gemini, Google Drive, and PDF.co
