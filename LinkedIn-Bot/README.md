# 🤖 LinkedIn Bot

> Send a topic via Telegram and automatically research, write, and publish a viral LinkedIn post.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The LinkedIn Bot is an AI-powered automation built in n8n that automatically:

- Receives topics via Telegram (text or voice message)
- Transcribes voice notes using OpenAI Whisper
- Researches the topic with GPT-4o Search for current data and trends
- Writes a viral LinkedIn post using Claude Sonnet 4 with conversion-optimized prompts
- Publishes directly to your LinkedIn profile via OAuth

It's designed for busy professionals who want to maintain consistent LinkedIn presence without spending hours writing and researching.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 💬 **Telegram Interface** | Send topics as text or voice messages from anywhere |
| 🎙️ **Voice Transcription** | OpenAI Whisper converts voice notes to text |
| 🔍 **Live Research** | GPT-4o Search finds current stats, case studies, and expert opinions |
| ✍️ **Viral Post Writing** | Claude Sonnet 4 crafts engagement-optimized posts with proven frameworks |
| 📤 **Auto-Publishing** | Posts directly to LinkedIn via OAuth - no copy-paste needed |
| 🔒 **User Validation** | Chat ID verification ensures only you can trigger posts |

## Workflow Architecture

```
Telegram Message (Text or Voice)
           ↓
    Validate User (Chat ID)
           ↓
    ┌──────┴──────┐
    ↓             ↓
  Text         Voice
    ↓             ↓
setMessage    Get File → Transcribe (Whisper)
    ↓             ↓
    └──────┬──────┘
           ↓
      Set Topic
           ↓
   Research (GPT-4o Search)
           ↓
   Post Writer (Claude Sonnet 4)
           ↓
   Publish to LinkedIn
```

The workflow handles both text and voice inputs, converging into a single research and writing pipeline before publishing.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Telegram](https://telegram.org) (create a bot via BotFather)
- [OpenAI](https://platform.openai.com) (for Whisper transcription and GPT-4o Search)
- [Anthropic](https://anthropic.com) (for Claude Sonnet 4)
- [LinkedIn](https://linkedin.com) (OAuth2 API access)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **Telegram**: Create a bot via @BotFather and add the API token
2. **OpenAI**: Add your API key for Whisper and GPT-4o Search
3. **Anthropic**: Add your API key for Claude Sonnet 4
4. **LinkedIn**: Set up OAuth2 credentials with posting permissions

### 4. Set Your Chat ID

Update the `If` node with your Telegram chat ID:
1. Send a message to your bot
2. Check the workflow execution to find your chat ID
3. Update the condition to match your chat ID

### 5. Connect Your LinkedIn

1. Update the `Create a post` node with your LinkedIn person ID
2. Authorize the OAuth2 connection
3. Test with a simple post to verify permissions

## The Post Writing Framework

The bot uses a comprehensive viral post framework including:

- **Hook formulas**: Problem-driven, outcome-focused, numbers-driven, story-based
- **Content types**: Educational (50%), Authority-building (30%), Lead-generating (20%)
- **Structure**: Hook → Core value → Personal sauce → CTA
- **Power words**: Proven, secret, exclusive, instant, framework, system

## Example Use Cases

- **Thought Leaders**: Share ideas on-the-go via voice notes
- **Agency Owners**: Maintain consistent posting while traveling
- **Consultants**: Turn client insights into content instantly
- **Executives**: Post about industry trends without writing from scratch

## Pro Tips

- Use voice messages when ideas strike - the transcription handles the rest
- Be specific with topics: "AI automation pricing strategies" beats "AI"
- The research step pulls 2025 data - great for timely, relevant posts
- Review posts in LinkedIn before they go live by changing the node to draft mode
- Set up multiple Telegram bots for different LinkedIn accounts

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Telegram, OpenAI, Anthropic Claude, and LinkedIn API
