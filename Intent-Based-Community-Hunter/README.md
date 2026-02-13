# 🎯 Intent-Based Community Hunter

> Turn LinkedIn post comments into qualified leads with AI-powered intent classification and personalized outreach drafts.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Intent-Based Community Hunter is an AI-powered automation built in n8n that automatically:

- Scrapes all comments from any LinkedIn post via Apify
- Analyzes each comment for buying intent using Gemini AI
- Classifies leads as High Intent, Curious, or Supportive
- Filters to only high-intent prospects asking for demos, pricing, or features
- Drafts personalized outreach messages referencing their specific comment
- Saves qualified leads with drafted messages to Airtable CRM

It's designed for sales professionals, agency owners, and founders who want to find warm leads hiding in plain sight on LinkedIn.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔗 **Comment Scraping** | Apify extracts all comments and replies from any LinkedIn post URL |
| 🧠 **Intent Classification** | Gemini 3 Flash categorizes each comment as High Intent, Curious, or Supportive |
| 🎯 **Smart Filtering** | Only passes through leads showing genuine buying signals |
| ✍️ **Personalized Drafts** | Gemini 3 Pro writes custom outreach referencing their exact comment |
| 💾 **CRM Integration** | Saves lead name, profile, comment, and draft message to Airtable |
| 📋 **Context-Aware** | Uses post content and your offer to craft relevant messages |

## Workflow Architecture

```
Form Submission (LinkedIn Post URL + Intent) → Scrape Comments (Apify)
                                                       ↓
                                            Get Scraper Results
                                                       ↓
                                    Classify Comment Intent (Gemini 3 Flash)
                                                       ↓
                                            Format Lead Data
                                                       ↓
                                     Filter High Buying Intent Only
                                                       ↓
                                    Draft Outreach Message (Gemini 3 Pro)
                                                       ↓
                                        Save to CRM (Airtable)
```

The workflow processes each comment individually, classifying intent and only advancing high-quality leads to the outreach drafting stage.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Apify](https://apify.com) (LinkedIn comment scraping actor)
- [Google AI Studio](https://aistudio.google.com) (for Gemini access)
- [Airtable](https://airtable.com) (for lead storage and management)

### 2. Import the Workflow

1. Download `Intent-Based-Community-Hunter.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **Apify**: Connect your Apify account and authorize the LinkedIn Post Comments Scraper actor
2. **Google Gemini**: Add your API key for Gemini 3 Flash and Gemini 3 Pro
3. **Airtable**: Create a base with columns: `Name`, `Drafted Message`, `Linkedin Profile`, `LinkedIn Post`, `Comments`

### 4. Configure the Form

The form collects:
- **LinkedIn Post URL**: The post to mine for leads
- **Intent**: What you're looking for (e.g., "Likely to buy an n8n automation")
- **Post Content**: The original post text for context
- **Is this your post?**: Helps the AI adjust outreach tone

### 5. Customize Intent Categories

Edit the `Classify Comment Intent` node to adjust the classification criteria:
- **High Buying Intent**: Asking for price, demo, meeting, specific features
- **Curious**: Asking general questions
- **Supportive**: Congratulations, agreeing, generic praise

## Example Use Cases

- **Agency Owners**: Mine competitor or industry posts for prospects asking about services you offer
- **SaaS Founders**: Find users complaining about problems your product solves
- **Consultants**: Identify business owners seeking advice in your specialty
- **Course Creators**: Spot learners asking questions your content answers

## Pro Tips

- Target viral posts in your niche - more comments means more potential leads
- Set specific intents like "looking for automation help" rather than generic ones
- Use posts from industry thought leaders where your ideal customers hang out
- Review and personalize the AI drafts before sending - add your unique touch
- Track response rates in Airtable to optimize your outreach approach
- Works on both your own posts and other people's posts

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Apify, Google Gemini, and Airtable
