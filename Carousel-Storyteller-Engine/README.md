# 📱 Carousel Storyteller Engine

> Turn any topic into a viral LinkedIn/Instagram carousel with AI-generated slides, captions, and consistent visual design.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

Carousel Storyteller Engine is an AI-powered automation built in n8n that automatically:

- Accepts a topic and visual style via web form
- Uses Perplexity AI to generate a complete 8-10 slide carousel strategy (hooks, value slides, CTAs)
- Creates headlines, body copy, and visual element suggestions for each slide
- Generates LinkedIn and Instagram captions with hashtags
- Creates a base design template using Gemini image generation
- Renders each slide with consistent styling using AI image editing
- Uploads all slides to Google Drive and saves the campaign to Airtable

It's designed for content creators, marketers, and agencies who want to produce professional carousel content without design skills.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 🎯 **6 Visual Styles** | Choose from Minimalist Apple, Bold Streetwear, Luxury Editorial, SaaS Dark Mode, Neo-Brutalist, or Retro 90s |
| 🧠 **AI Content Strategy** | Perplexity generates viral carousel structure with hooks, retention, and CTAs |
| 🖼️ **Consistent Design** | Gemini creates a base template, then renders each slide with matching style |
| 📝 **Auto-Captions** | Generates platform-optimized captions for LinkedIn (professional) and Instagram (casual + hashtags) |
| 📁 **Organized Output** | Creates Google Drive folder with numbered slides, saves campaign to Airtable |
| 📐 **Mobile-First** | All slides are 4:5 portrait orientation optimized for mobile scrolling |

## 🏗️ Workflow Architecture

```
Form Trigger (Topic + Style)
        ↓
Perplexity AI (Carousel Strategy)
        ↓
┌───────┴───────┬───────────┐
↓               ↓           ↓
Gemini Base   Content     GDrive Folder
Design        JSON
        ↓
    Merge All Data
        ↓
Loop: For Each Slide
    ↓
    Gemini Edit (Render Slide)
    ↓
    Upload to Drive
        ↓
Aggregate → Save to Airtable
```

The workflow generates content and base design in parallel, then loops through each slide to render and upload before saving the complete campaign.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [OpenRouter](https://openrouter.ai) (for Perplexity AI access)
- [OpenAI](https://platform.openai.com) (for JSON parsing with GPT-4)
- [Google AI Studio](https://aistudio.google.com) (for Gemini image generation)
- [Google Drive](https://drive.google.com) (for slide storage)
- [Airtable](https://airtable.com) (for campaign tracking)

### 2️⃣ Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **OpenRouter**: Add your API key for Perplexity access
2. **OpenAI**: Add your API key for GPT-4 JSON parsing
3. **Google Gemini**: Add your API key for image generation
4. **Google Drive**: Authorize OAuth2 and create a folder "Carousel Storyteller Engine"
5. **Airtable**: Create a base with columns: `Input Topic`, `Linkedin Caption`, `IG Caption`, `Status` (Posted/In Review), `Slides` (URL)

### 4️⃣ Update Folder ID

In the "GDrive: Create Slide Folder" node, update the parent folder ID to your "Carousel Storyteller Engine" folder.

## 🧪 Example Use Cases

- **LinkedIn Creators**: Turn insights into swipeable carousel posts that drive engagement
- **Marketing Agencies**: Produce client carousel content in minutes instead of hours
- **Course Creators**: Create educational slide decks for social media distribution
- **Personal Brands**: Maintain consistent visual identity across all carousel content

## 💡 Pro Tips

- The 6 visual styles are highly customizable - edit the form options for your brand aesthetic
- Perplexity's research capabilities mean it can create carousels on current events and trends
- Use the Airtable "In Review" status to queue content for approval before posting
- The base design template ensures visual consistency - great for brand recognition
- Adjust the carousel card count (8-10) in the LLM prompt for shorter or longer content

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, Perplexity AI, Google Gemini, Google Drive, and Airtable
