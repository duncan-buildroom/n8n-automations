# 🎯 Smart Lead Scoring & Routing

> AI-powered lead qualification system that validates identities, scores business potential, and tracks engagement in real-time.

One of the systems I teach inside [The Build Room](https://www.skool.com/build-room) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Smart Lead Scoring & Routing system is an n8n automation that automatically:

- Captures leads via customizable web forms
- Verifies email deliverability using Apify Email Verifier
- Validates lead identity through multi-source AI research (5-8 web searches)
- Crawls company websites to understand business context
- Scores lead quality based on completeness and business fit
- Tracks engagement signals (email opens, link clicks) in real-time
- Routes and stores qualified leads to Airtable with composite scores

It's designed for sales teams who want to instantly qualify inbound leads and prioritize outreach based on AI-validated confidence and engagement.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 📝 **Lead Capture Form** | Collects name, email, company URL, company size, job title, and industry |
| ✉️ **Email Verification** | Apify Email Verifier checks deliverability before processing |
| 🔍 **Identity Validation** | AI agent performs 5-8 web searches to verify lead authenticity |
| 🏢 **Company Enrichment** | Apify Website Crawler extracts company context for scoring |
| 📊 **Dual Scoring System** | Confidence score (identity) + quality score (business fit) combined |
| 📈 **Engagement Tracking** | Webhook captures email opens (+5 pts) and link clicks (+10 pts) |
| 💾 **Lead Pipeline** | Airtable stores leads with running scores and deduplication |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                      PHASE 1: LEAD CAPTURE                          │
├─────────────────────────────────────────────────────────────────────┤
│  Form Submission → Verify Email (Apify) → Check If Valid            │
│                              ↓                                      │
│                    Filter Invalid Emails                            │
└─────────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 2: ENRICHMENT (Parallel)                     │
├─────────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┐    ┌─────────────────────────────┐    │
│  │  Lead Validation Agent  │    │  Crawl Company Website      │    │
│  │  (GPT-5-mini + Sonar)   │    │  (Apify Content Crawler)    │    │
│  │                         │    │                             │    │
│  │  • LinkedIn search      │    │  • Extract site text        │    │
│  │  • Company verification │    │  • Truncate to 1000 chars   │    │
│  │  • Digital footprint    │    │                             │    │
│  │  • Confidence 0-100     │    │                             │    │
│  └─────────────────────────┘    └─────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────────┐
│                    PHASE 3: SCORING & STORAGE                       │
├─────────────────────────────────────────────────────────────────────┤
│  Merge Data → Lead Quality Scorer (Gemini 3 Pro) → Calculate Base   │
│                              ↓                                      │
│         Lead Base Score = (Confidence/100) × Quality Score          │
│                              ↓                                      │
│              Check If New → Create or Update in Airtable            │
└─────────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────────┐
│                   PHASE 4: ENGAGEMENT TRACKING                      │
├─────────────────────────────────────────────────────────────────────┤
│  Webhook Trigger → Route by Action Type                             │
│         ↓                    ↓                     ↓                │
│   Email Open (+5)    Link Click (+10)    Generate/Send Email        │
│         └──────────────────┴─────────────────────┘                  │
│                              ↓                                      │
│                 Update Engagement Score in Airtable                 │
└─────────────────────────────────────────────────────────────────────┘
```

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Apify](https://apify.com) (Email Verifier + Website Content Crawler actors)
- [OpenRouter](https://openrouter.ai) (GPT-5-mini + Perplexity Sonar Reasoning)
- [Google AI Studio](https://makersuite.google.com) (Gemini 3 Pro)
- [Airtable](https://airtable.com) (lead storage and tracking)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Airtable

Create a base with a **Leads** table containing:
- Full Name, Email, Company URL, Company Size, Job Title, Industry
- Status (New, Contacted, Qualified, etc.)
- Confidence Score, Confidence Summary
- Lead Base Score, Engagement Score
- Company Text

### 4. Set Up the Lead Capture Form

1. Configure the form trigger with your branding
2. Company Size dropdown: 1-50, 51-100, 101+
3. Deploy the form URL to your website or landing pages

### 5. Configure Credentials

1. **Apify**: Add your API key for email verification and web crawling
2. **OpenRouter**: Add your API key for GPT-5-mini and Perplexity Sonar
3. **Google Gemini**: Add your API key for quality scoring
4. **Airtable**: Authorize OAuth2 and update base/table IDs

### 6. Customize Scoring Logic

1. Update "About My Company" in the Set node to describe your business
2. Adjust the Lead Quality Scorer prompt for your ideal customer profile
3. Modify engagement point values as needed (default: opens +5, clicks +10)

## Example Use Cases

- **SaaS Companies**: Qualify trial signups based on company size and tech fit
- **Agencies**: Score inbound leads by budget potential and service alignment
- **B2B Sales**: Prioritize outreach based on validated identity and engagement
- **Consultants**: Filter tire-kickers from serious prospects automatically

## Pro Tips

- The validation agent performs 5-8 searches - leads with no digital footprint score low
- Email opens and link clicks compound over time, surfacing engaged prospects
- Use the Company Text field to understand what prospects actually do
- Lead Base Score combines identity confidence with business fit - prioritize high scores
- Set up Airtable views to filter by score thresholds for your sales team
- Connect webhook tracking pixels to your email campaigns for automatic engagement updates

---

## Want to Build & Sell AI Automations Like This?

Join **The Build Room** and learn to build and sell AI automations - from $49 templates to $3K+ clients in 30 days.

[Join The Build Room](https://www.skool.com/build-room)

---

Built with n8n, Apify, OpenRouter (GPT-5-mini, Perplexity Sonar), Google Gemini 3 Pro, and Airtable
