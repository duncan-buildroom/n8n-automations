# 🎫 AI-Powered Customer Feedback & Feature Request Triage

> Automatically collect, classify, and route customer feedback from App Store, Discord, and Twitter into prioritized support tickets.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

AI-Powered Customer Feedback Triage is an automation built in n8n that automatically:

- Collects customer feedback from App Store reviews, Discord support channels, and Twitter/X mentions
- Filters for recent messages (last 48 hours)
- Uses AI to classify each message by priority, type, and sentiment
- Auto-generates ticket titles and descriptions
- Routes tickets to the right team member based on specialization (Frontend, Backend, QA, Product, Design)
- Creates structured support tickets in Airtable
- Generates comprehensive analytics reports with sentiment analysis and feature request prioritization

It's designed for product teams, SaaS companies, and app developers who want to stay on top of customer feedback without drowning in manual triage.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 📱 **Multi-Channel Collection** | Pulls feedback from App Store reviews, Discord, and Twitter/X simultaneously |
| 🏷️ **AI Classification** | GPT categorizes by priority (urgent/high/medium/low), type (bug/feature/feedback/support), and sentiment |
| 🎯 **Smart Routing** | Auto-assigns tickets to team members based on issue type and specialization |
| 📝 **Auto-Generated Tickets** | AI writes clear ticket titles and detailed descriptions from raw feedback |
| 📊 **Analytics Reports** | Generates executive summaries with sentiment trends, topic analysis, and feature request priorities |
| 🗄️ **Airtable Integration** | Creates tickets and stores reports in a structured database for team collaboration |

## 🏗️ Workflow Architecture

```
Schedule (Every 2 Days)
        ↓
┌───────┼───────┐
↓       ↓       ↓
Discord Twitter App Store
        ↓
    Merge All Sources
        ↓
    AI Classification
    (Priority, Type, Sentiment, Assignee)
        ↓
    Create Airtable Tickets
        ↓
    Aggregate Feedback
        ↓
    AI Analytics Report
    (Executive Summary, Sentiment, Topics, Feature Priorities)
        ↓
    Save Report to Airtable
```

The workflow runs every 2 days, pulls from all feedback channels, classifies each item with AI, creates individual tickets, then generates a comprehensive analytics report.

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [OpenAI](https://platform.openai.com) (for GPT classification and report generation)
- [Airtable](https://airtable.com) (for ticket and report storage)
- [Discord](https://discord.com/developers) (Bot API for fetching support messages)
- [Twitter/X](https://developer.twitter.com) (API for searching mentions)

### 2️⃣ Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **OpenAI**: Add your API key for GPT access
2. **Discord Bot**: Create a bot and add it to your server with message read permissions
3. **Twitter/X**: Set up OAuth2 credentials with search permissions
4. **Airtable**: Create a base called "Support & Feedback Hub" with two tables:
   - **Tickets**: `Ticket Title`, `Description`, `Original Message`, `Status` (Open/In Progress/Resolved/Closed), `Priority` (low/medium/high/urgent), `Type` (bug/feature_request/feedback/support), `Sentiment` (positive/negative/neutral), `Assigned to` (linked to Team Members table)
   - **Summaries**: `Executive Summary`, `Sentiment Overview`, `Topic Analysis`, `Feature Request`, `Highlights`

### 4️⃣ Configure Your App & Channels

1. Update the App Store `appId` in the "Set: App Store Parameters" node
2. Update the Discord server and channel IDs
3. Update the Twitter search query (e.g., `@yourSupport`)

### 5️⃣ Set Up Team Routing

Edit the AI classification prompt to include your team members and their specializations for auto-assignment.

## 🧪 Example Use Cases

- **Mobile App Teams**: Automatically triage App Store reviews and route bugs to engineering
- **SaaS Companies**: Collect Discord and Twitter feedback, prioritize feature requests for product roadmap
- **Support Teams**: Reduce manual ticket creation and ensure nothing falls through the cracks
- **Product Managers**: Get weekly analytics reports on customer sentiment and trending topics

## 💡 Pro Tips

- Customize the team member list and routing logic in the AI classification prompt
- Add more feedback sources (email, Intercom, Zendesk) by following the same pattern
- Use Airtable views to create dashboards for different teams (Engineering, Product, Support)
- Set up Airtable automations to notify team members when they're assigned a ticket
- Adjust the schedule trigger based on your feedback volume (daily for high-volume apps)

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, OpenAI GPT, Airtable, Discord, and Twitter/X
