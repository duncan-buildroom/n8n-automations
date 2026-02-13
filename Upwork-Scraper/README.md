# 💼 Upwork Scraper

> Automatically scrape Upwork jobs, filter for relevance with AI, and generate personalized icebreaker messages.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Upwork Scraper is an n8n automation that automatically:

- Scrapes active freelance jobs from Upwork via RapidAPI
- Cleans and normalizes job data (title, description, budget, skills, location)
- Uses GPT-4o-mini to filter jobs based on your ideal project criteria
- Generates confident, personalized icebreaker messages for relevant jobs
- Stores qualified leads in Airtable with status tracking

It's designed for freelancers and agencies who want to find high-quality Upwork leads without manually scrolling through hundreds of irrelevant posts.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 🔍 **Smart Job Scraping** | Pulls fresh jobs from Upwork's active listings via RapidAPI |
| 🧹 **Data Cleaning** | Normalizes budget formats, skills arrays, and location data |
| 🤖 **AI Job Filtering** | GPT-4o-mini evaluates each job against your ideal project criteria |
| 💬 **Icebreaker Generator** | Creates confident, personalized intro messages referencing relevant experience |
| 📊 **Airtable CRM** | Stores qualified leads with job details, icebreaker, and application status |
| 🎯 **Custom Criteria** | Fully customizable filter prompt for your specific niche and skills |

## Workflow Architecture

```
Manual Trigger
       ↓
Scrape Upwork Jobs (RapidAPI)
       ↓
Clean & Normalize Data (Code Node)
       ↓
AI Job Filter (GPT-4o-mini)
  - Evaluates relevance
  - Generates icebreaker
       ↓
Filter (Keep only relevant jobs)
       ↓
Store in Airtable
  - Job details
  - Icebreaker message
  - Status: Intake
```

The workflow processes each job individually, allowing the AI to craft personalized icebreakers based on the specific job requirements.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [RapidAPI](https://rapidapi.com) (for Upwork Jobs API access)
- [OpenAI](https://platform.openai.com) (for GPT-4o-mini)
- [Airtable](https://airtable.com) (for lead storage)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **RapidAPI**: Add your API key as an HTTP Header Auth credential (x-rapidapi-key)
2. **OpenAI**: Add your API key for GPT-4o-mini
3. **Airtable**: Create a base with columns: Job Title, Job Description, Budget, Skills, Client Location, Icebreaker Message, Original URL, Status

### 4. Customize Your Filter Criteria

Update the AI Job Filter system prompt to match your skills and ideal projects:
- Add your relevant platforms and tools
- Define what types of projects to exclude
- Adjust the icebreaker style to match your voice

### 5. Configure Search Parameters

In the scrapeUpwork node, customize:
- `search`: Your target keyword (e.g., "automation", "n8n", "Airtable")
- `limit`: Number of jobs to fetch per run

## The Filtering Framework

The default filter is optimized for automation engineers and includes:

**Relevant Skills**: Airtable, ClickUp, ChatGPT, Make, Monday.com, Zapier, LinkedIn, Google Sheets, n8n

**Exclusions**:
- Full-stack app development
- Python, Telegram, WhatsApp, Facebook bots
- Virtual assistant work
- Tiny projects (<10 minutes)
- Jobs where tools are mentioned incidentally

**Icebreaker Formula**: References specific relevant experience with scale/results

## Example Use Cases

- **Automation Freelancers**: Find clients who need no-code integrations and workflow automation
- **Agency Owners**: Generate a steady pipeline of qualified Upwork leads
- **Consultants**: Identify high-budget projects in your niche
- **Side Hustlers**: Efficiently filter through jobs while working full-time

## Pro Tips

- Run the workflow hourly during peak posting times (9am-11am EST)
- Customize the icebreaker examples with your actual case studies
- Set up Airtable views to separate Intake, Applied, Won, and Declined
- Use the URL field to quickly open and apply to jobs
- Adjust the search keyword based on what clients actually search for

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, RapidAPI, OpenAI GPT-4o-mini, and Airtable
