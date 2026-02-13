# 🔬 Reddit Insights

> Mine any subreddit for business opportunities and turn community discussions into actionable product ideas.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

Reddit Insights is an n8n automation that automatically:

- Pulls top posts from any subreddit you choose
- Uses GPT-4.1 to extract problems, frustrations, ideas, and opportunities from discussions
- Passes insights through a "Business Coach" AI to generate specific feature implementations
- Stores all opportunities in Airtable with problem context and impact ratings
- Sends a formatted summary to Slack for team review

It's designed for product teams, founders, and marketers who want to turn real customer conversations into product roadmap items.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 📡 **Subreddit Mining** | Pull top posts from any subreddit relevant to your industry |
| 🔍 **Problem Extraction** | GPT-4.1 identifies core problems and frustrations from discussions |
| 💡 **Idea Detection** | Captures high-impact solutions and innovations mentioned by users |
| 🎯 **Business Translation** | AI "Business Coach" converts insights into specific feature proposals |
| 📊 **Impact Assessment** | Rates implementation complexity and potential business impact |
| 💬 **Slack Notifications** | Sends formatted opportunity summaries to your team channel |

## Workflow Architecture

```
Manual Trigger
       ↓
Get Reddit Posts (subreddit API)
       ↓
Post Researcher (GPT-4.1)
  - Extract: problem, frustration, ideas, possibilities
       ↓
Business Coach (GPT-4.1)
  - Generate: feature name, description, target problem
  - Assess: complexity, impact, business application
       ↓
    ┌──────┴──────┐
    ↓             ↓
Airtable       Aggregate
(Store each)      ↓
              Format Message
                  ↓
              Slack Summary
```

The two-stage AI analysis first extracts raw insights, then translates them into actionable business opportunities.

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Reddit](https://reddit.com) (OAuth2 API access)
- [OpenAI](https://platform.openai.com) (for GPT-4.1)
- [Airtable](https://airtable.com) (for opportunity storage)
- [Slack](https://slack.com) (for team notifications)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Configure Credentials

1. **Reddit**: Set up OAuth2 credentials via Reddit's developer portal
2. **OpenAI**: Add your API key for GPT-4.1 access
3. **Airtable**: Create a base with columns: Name, Description, Problem, Frustration, Ideas, Possibilities, Business Application, Impact, Complexity, Status
4. **Slack**: Connect via OAuth2 and select your target channel

### 4. Choose Your Subreddit

In the "Get many posts" node, update:
- `subreddit`: Your target community (e.g., "saas", "smallbusiness", "startups")
- `limit`: Number of posts to analyze per run
- `category`: "top", "hot", or "new"

### 5. Customize the Business Coach

Update the Business Coach system prompt to match your business:
- Replace "real estate lead generation" with your industry
- Adjust the feature evaluation criteria
- Customize the output format for your team's needs

## The Analysis Framework

**Post Researcher extracts:**
- Problem: Core challenge being discussed
- Frustration: Emotional pain points and difficulties
- Ideas: Solutions and innovations mentioned
- Possibilities: Adjacent opportunities and markets

**Business Coach generates:**
- Feature Name: Specific, actionable feature proposal
- Description: Detailed implementation approach
- Target Problem: Which pain point this solves
- Business Application: How it helps your target customer
- Complexity: Low/Medium/High implementation effort
- Impact: Revenue/retention/acquisition benefit

## Example Use Cases

- **SaaS Founders**: Mine r/saas, r/startups for feature ideas
- **E-commerce Brands**: Track r/ecommerce, r/shopify for pain points
- **Agency Owners**: Monitor r/marketing, r/ppc for service opportunities
- **Product Managers**: Research r/userexperience, r/productmanagement for UX insights

## Pro Tips

- Start with niche subreddits where your ideal customers hang out
- Run weekly to catch emerging trends and recurring complaints
- Use the complexity rating to prioritize quick wins
- Cross-reference opportunities that appear across multiple subreddits
- Set up Airtable views by complexity and impact for prioritization

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Reddit API, OpenAI GPT-4.1, Airtable, and Slack
