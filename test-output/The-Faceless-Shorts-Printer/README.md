# 🎬 The "Faceless" Shorts Printer

> Fully automated faceless video production: from niche topic to rendered short in one workflow.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Faceless Shorts Printer is an n8n automation that automatically:

- Researches viral stories in your chosen niche using Perplexity
- Writes a 90-second script optimized for TTS delivery
- Generates professional voiceover audio via WaveSpeed/ElevenLabs
- Transcribes audio with timestamps and emotion detection
- Creates a visual storyboard with scene-by-scene prompts
- Generates consistent character images and scene backgrounds
- Morphs images into video clips with motion
- Renders the final video with audio using Creatomate

It's designed for faceless content creators who want to scale video production without appearing on camera.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔍 **Story Research** | Perplexity finds viral stories in your niche |
| ✍️ **Script Writing** | Gemini condenses stories into 90-second TTS scripts |
| 🎙️ **Voice Generation** | WaveSpeed/ElevenLabs creates natural-sounding audio |
| 📝 **Smart Transcription** | Timestamps, emotions, and speaker detection |
| 🎨 **Visual Direction** | AI creates image/video prompts per scene |
| 🖼️ **Consistent Characters** | Main character reference keeps visuals coherent |
| 🎥 **Image-to-Video** | Morphs static images into motion clips |
| 🎞️ **Final Render** | Creatomate assembles audio + video into MP4 |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│               PHASE 1: TRIGGER & CONFIGURATION                      │
├─────────────────────────────────────────────────────────────────────┤
│  Manual Trigger → Set: Define Niche                                 │
│  (e.g., "Relationship horror stories from reddit")                  │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│              PHASE 2: STORY RESEARCH & SCRIPT WRITING               │
├─────────────────────────────────────────────────────────────────────┤
│  LLM: Generate Full Story (Perplexity)                              │
│  • Searches for viral stories in niche                              │
│  • Finds high-engagement Reddit/social content                      │
│                              ↓                                      │
│  Gemini: Write Viral Script                                         │
│  • Condenses into 90-second TTS script                              │
│  • Optimizes for voice delivery                                     │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                PHASE 3: TEXT-TO-SPEECH GENERATION                   │
├─────────────────────────────────────────────────────────────────────┤
│  Create TTS Task (WaveSpeed/ElevenLabs)                             │
│  → Wait → Check Status → Loop until ready                           │
│  → Set: Audio URL                                                   │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│            PHASE 4: AUDIO TRANSCRIPTION & VISUAL PLANNING           │
├─────────────────────────────────────────────────────────────────────┤
│  Download Audio → Fix MIME Type → Upload to Gemini                  │
│                              ↓                                      │
│  API: Transcribe Audio (Gemini 3 Flash)                             │
│  • Timestamped segments                                             │
│  • Emotion detection (Happy, Sad, Angry, Neutral)                   │
│  • Speaker identification                                           │
│                              ↓                                      │
│  Gemini: Visual Director                                            │
│  • Creates image/video prompts per scene                            │
│  • Determines if scene needs character or just background           │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 5: IMAGE GENERATION                        │
├─────────────────────────────────────────────────────────────────────┤
│  Main Character Image (Kie AI)                                      │
│  • Creates consistent character reference                           │
│                              ↓                                      │
│  Split: Scenes to Items → For Each Scene:                           │
│         ↓                           ↓                               │
│  Contains Character?          Background Only?                      │
│         ↓                           ↓                               │
│  Character + Scene Image     Scene Background                       │
│         └───────────────────────────┘                               │
│                              ↓                                      │
│              Sort by Scene Number → Aggregate                       │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│               PHASE 6: VIDEO GENERATION & FINAL RENDER              │
├─────────────────────────────────────────────────────────────────────┤
│  Merge: Images + Prompts → Match Images to Prompts                  │
│                              ↓                                      │
│  API: Create Videos (Image-to-Video morphing)                       │
│                              ↓                                      │
│  Merge: Audio + Videos → Build Creatomate Payload                   │
│                              ↓                                      │
│  API: Render Final Video (Creatomate)                               │
│  • Combines sequential video clips                                  │
│  • Overlays audio track                                             │
│  • Outputs final MP4                                                │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Perplexity AI](https://perplexity.ai) (story research)
- [Google AI Studio](https://makersuite.google.com) (Gemini 3 for scripts, transcription, visual direction)
- [WaveSpeed](https://wavespeed.ai) or [ElevenLabs](https://elevenlabs.io) (text-to-speech)
- [Kie AI](https://kie.ai) (image generation with nano-banana)
- [Creatomate](https://creatomate.com) (final video rendering)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Creatomate Template

1. Create a video template in Creatomate
2. Add an audio element named "Audio-JNM"
3. Add a composition named "Composition-C5Z" for video elements
4. Update the template ID in the workflow

### 4. Configure Credentials

1. **Google Gemini**: Add your API key for script writing and transcription
2. **WaveSpeed/ElevenLabs**: Add your API key for voice generation
3. **Kie AI**: Add your API key for image generation
4. **Creatomate**: Add your API key for final rendering

### 5. Set Your Niche

Update the "Set: Define Niche" node with your content topic:
- "Relationship horror stories from reddit"
- "True crime stories"
- "Unexplained mysteries"
- "Revenge stories"

## Example Niches

| Niche | Content Type | Audience |
|-------|-------------|----------|
| Reddit Stories | AITA, relationship drama | Entertainment seekers |
| True Crime | Cold cases, mysteries | Mystery enthusiasts |
| Motivation | Success stories, comebacks | Self-improvement |
| History | Bizarre historical events | Education seekers |

## Pro Tips

- The main character image is used as a reference for consistency across scenes
- Emotion detection helps the visual director match scene mood
- Scene sorting ensures video clips render in the correct order
- Scripts are optimized for 90 seconds - perfect for YouTube Shorts
- Creatomate handles the heavy lifting of syncing audio to video
- Run the workflow manually first to test your niche before scheduling
- Review generated scripts before rendering - edit as needed

---

## Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[Join The Build Room](https://www.skool.com/build-room)

---

Built with n8n, Perplexity AI, Google Gemini 3, WaveSpeed/ElevenLabs, Kie AI, and Creatomate
