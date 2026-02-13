# 🎭 The "Persona" Infinite Storyteller

> Turn trending Reddit stories into faceless video content with a Gen-Z storyteller persona.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Persona Infinite Storyteller is an n8n automation that automatically:

- Accepts any Reddit post URL
- Researches and verifies the story using Perplexity
- Generates a viral 60-second script with psychological hooks
- Converts the script into 12 visual scenes with Gen-Z storyteller persona
- Creates consistent character images across all scenes
- Produces image prompts and video prompts for each scene
- Matches images to spoken text for video assembly

It's designed for faceless content creators who want to turn trending Reddit stories into TikTok/Shorts content.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔗 **Reddit Integration** | Parses any Reddit URL and fetches post data |
| 🔍 **Story Research** | Perplexity verifies facts and finds sources |
| ✍️ **Viral Scripts** | 60-second scripts with scroll-stopping hooks |
| 🎭 **Gen-Z Persona** | "FaceTime with bestie" storytelling style |
| 🖼️ **12 Scene Storyboard** | Complete visual breakdown with image prompts |
| 🎬 **Video Prompts** | Motion and action directions for each scene |

## The 12-Scene Structure

| Scene | Purpose |
|-------|---------|
| 1 | **The Hook** - Scroll-stopper opening |
| 2-10 | **The Story** - Small, punchy updates |
| 11 | **The Climax** - Result and resolution |
| 12 | **The Kicker** - Reaction and engagement prompt |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                       PHASE 1: INPUT                                │
├─────────────────────────────────────────────────────────────────────┤
│  Form: Enter Reddit Post URL                                        │
│                    ↓                                                │
│  Code: Parse URL → Extract subreddit + postId                       │
│                    ↓                                                │
│  Reddit API: Get Post Data                                          │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 2: RESEARCH & SCRIPT                         │
├─────────────────────────────────────────────────────────────────────┤
│  LLM: Generate Full Story (Perplexity Sonar Pro)                    │
│  • Research trending context                                        │
│  • Verify facts from credible sources                               │
│  • Write 60-second viral script (160-190 words)                     │
│                    ↓                                                │
│  Output:                                                            │
│  • headline (5-word clickbait title)                                │
│  • event_date                                                       │
│  • virality_hook (psychological trigger)                            │
│  • narrative_script                                                 │
│  • source_links                                                     │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 3: VISUAL STORYBOARD                         │
├─────────────────────────────────────────────────────────────────────┤
│  Gemini: Create 12-Scene Storyboard                                 │
│  • Adapts script to Gen-Z persona                                   │
│  • 10-17 words spoken text per scene                                │
│  • Image prompts with consistent character                          │
│  • Video prompts with dynamic motion                                │
│                    ↓                                                │
│  Character: "The storyteller (natural woman in her 20s)"            │
│  Style: Casual, relatable, not glammed-up                           │
│  Camera: Handheld/selfie feel                                       │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 4: IMAGE GENERATION                          │
├─────────────────────────────────────────────────────────────────────┤
│  Split Out: 12 Scenes → Individual Items                            │
│                    ↓                                                │
│  Kie AI: Generate Character Images                                  │
│  • Wait → Check Status → Loop until complete                        │
│                    ↓                                                │
│  Aggregate: Video Prompts + Spoken Text                             │
│                    ↓                                                │
│  Code: Match Images to Prompts + Spoken Text                        │
└─────────────────────────────────────────────────────────────────────┘
```

## Script Rules

- **No Intros**: Start in the action, never "In this story..."
- **The Hook**: First sentence must stop the scroll
- **Sentence Structure**: Short, punchy, varying rhythm
- **Tone**: Empathetic, slightly dramatic, authoritative
- **Ending**: Lingering question or philosophical mic-drop

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Reddit API](https://www.reddit.com/prefs/apps) (OAuth2 for post access)
- [OpenRouter](https://openrouter.ai) (Perplexity Sonar Pro for research)
- [Google AI Studio](https://makersuite.google.com) (Gemini 3 Pro for storyboarding)
- [Kie AI](https://kie.ai) (image generation)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **Reddit**: Authorize OAuth2 for post data access
2. **OpenRouter**: Add your API key for Perplexity Sonar Pro
3. **Google Gemini**: Add your API key for storyboard generation
4. **Kie AI**: Add your API key for image generation

## Example Reddit Sources

| Subreddit | Content Type |
|-----------|-------------|
| r/AITA | Relationship drama, moral dilemmas |
| r/tifu | Embarrassing stories, fails |
| r/relationship_advice | Dating drama, breakups |
| r/pettyrevenge | Karma stories, justice |
| r/MaliciousCompliance | Workplace stories |

## Pro Tips

- Trending posts with high engagement make the best content
- The Gen-Z persona sounds improvised, not scripted
- Character consistency is maintained across all 12 scenes
- Video prompts include specific gestures and movements
- Stories with strong emotional hooks (betrayal, karma) perform best
- Review the 60-second script before generating visuals
- The "virality_hook" identifies the psychological trigger

---

## Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[Join The Build Room](https://www.skool.com/build-room)

---

Built with n8n, Reddit API, OpenRouter (Perplexity Sonar Pro), Google Gemini 3 Pro, and Kie AI
