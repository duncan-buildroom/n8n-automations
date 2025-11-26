🎬 Content Repurpose Automation

AI-powered n8n workflow that turns ANY short-form video into a fully-optimized YouTube/Twitter/Instagram post — automatically.

This workflow ingests a video URL from an RSS feed, downloads and transcribes it, generates a high-converting SEO YouTube description + clickbait title, uploads the media, and publishes to three social platforms in one shot.

Perfect for creators who want to multiply their content output without spending hours rewriting descriptions or cross-posting manually.

🎥 What This Workflow Does

This system automatically:

Pulls a new video URL from an RSS feed

Downloads the short-form video (TikTok, etc.)

Transcribes the audio using OpenAI

Generates:

a 40-character clickbait YouTube title, and

a ~200-word SEO-optimized description

Uploads the original video to Blotato

Publishes the finished content to:

YouTube (title + description + video)

Instagram (description + video)

Twitter/X (description + video)

All formatting, structuring, and compliance rules enforced automatically

Workflow source:

⚡ Overview

The Content Repurpose workflow is built for high-volume creators who need to transform raw short-form videos into multi-platform content with minimal effort.

It converts one piece of input (a single video URL) into a polished, platform-ready set of posts — using strict prompt rules that ensure consistency and SEO performance.

🧩 Features
Feature	Description
🎯 RSS Feed Trigger	Polls your RSS feed every hour to detect new video URLs.
⬇️ Video Downloader	Fetches video files using a TikTok downloader API.
🗣️ AI Transcription	Transcribes audio using OpenAI.
✍️ Title + Description Generator	Uses OpenRouter GPT models to produce a 40-char clickbait title + 200-word SEO description.
🧬 Strict JSON Output Parser	Ensures the AI output follows the exact JSON schema.
📤 Media Uploader	Uploads the video to Blotato + returns ready-to-post media URLs.
📡 3-Platform Auto-Publisher	Posts the video + AI description to YouTube, Instagram, and Twitter/X.
🔄 Fully Automated Flow	Zero manual steps: input arrives via RSS, output posts automatically.
🏗️ Workflow Architecture

RSS Feed → Set URL → TikTok Downloader → Video File → OpenAI Transcription → GPT Content Generator → Structured Output Parser → Upload Media → Merge → Publish to YouTube / Instagram / Twitter

Visual Breakdown

RSS Feed Trigger
Pulls latest video URLs from your feed every hour.

Video Downloader
Uses RapidAPI’s TikTok downloader endpoint to retrieve the actual video file.

Transcription (OpenAI)
Converts the video’s audio to text for downstream AI processing.

Content Generation (GPT via OpenRouter)
Produces two key deliverables:

40-character clickbait title

~200-word SEO-optimized video description
According to strict rules:

Must begin with:
Like + Comment "AI" and I will send you free training on how to build and sell AI automations.

Embeds keywords (AI automations, automation agency, n8n, Make.com, etc.)

Written in clear Hormozi-style language

No emojis

Structured Output Parser
Validates that the LLM returns perfect JSON.

Media Upload (Blotato)
Uploads the raw video file; returns a public media URL for posting.

Merge Node
Joins AI output with uploaded media URL.

Cross-Platform Publishing
Posts the final content to:

YouTube (title + description + video)

Instagram (description + video)

Twitter/X (description + video)

🔧 Setup Instructions
1. Required Accounts

OpenAI (for transcription)

OpenRouter (for GPT model generation)

Blotato (for media uploading + platform posting)

RapidAPI (TikTok downloader)

2. Import the Workflow

Download Content Repurpose.json

In n8n → Import Workflow

Add credentials for:

OpenAI

OpenRouter

RapidAPI (header auth)

Blotato

Update the RSS Feed URL inside the RSS Feed Trigger node

Enable workflow

🎯 Example Use Cases

YouTube Shorts → Long-form optimization

Daily TikTok → auto to YouTube, Twitter, IG

Hands-free repurposing for agencies

Creators who want consistent SEO descriptions without manual writing

🚀 Results You Can Expect

Save 30–60 minutes per video

Instant multi-platform posting

Consistent SEO + optimized titles

Uniform brand voice across platforms

Zero manual rewriting or copy/paste work

⭐ Why This Workflow Is Powerful

This system gives you a done-for-you content engine where:

You just publish short-form content

Your RSS feed picks it up

n8n handles everything — writing, uploading, and posting

It's essentially your own content publishing AI agent, running 24/7.
