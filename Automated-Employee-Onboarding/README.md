# 👋 Automated Employee Onboarding Sequencer

> Onboard new employees in minutes with automated Slack invites, Asana tasks, GitHub access, and manager notifications.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## 📹 Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## 🔍 Overview

Automated Employee Onboarding Sequencer is an automation built in n8n that automatically:

- Accepts new employee intake via web form (email + Slack ID)
- Looks up employee details and department from Airtable
- Routes to department-specific onboarding flows (Engineering vs. Marketing)
- Invites employees to the appropriate Slack channels
- Creates Asana onboarding tasks with subtasks (security training, ID collection, team intro)
- Sends beautiful HTML welcome emails
- Invites Engineering hires to GitHub organization
- Updates employee records with start date and manager link
- Notifies the department manager with an action checklist

It's designed for HR teams, operations managers, and growing companies who want to deliver a consistent, professional onboarding experience without manual coordination.

> 📺 **Free AI tutorials**: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## 🎨 Features

| Feature | Description |
|---------|-------------|
| 📝 **Self-Service Intake** | New hires complete a simple form with their work email and Slack ID |
| 🔀 **Department Routing** | Automatically routes to Engineering or Marketing onboarding flows |
| 💬 **Slack Provisioning** | Invites employees to department-specific channels automatically |
| ✅ **Asana Task Creation** | Creates onboarding task with subtasks (security video, ID pickup, Slack intro) |
| 🐙 **GitHub Access** | Engineering hires get invited to the GitHub organization |
| 📧 **Welcome Emails** | Sends professional HTML emails to new hires and their managers |
| 👔 **Manager Alerts** | Notifies managers with a checklist (schedule 1:1, assign buddy, etc.) |

## 🏗️ Workflow Architecture

```
Form Trigger (Email + Slack ID)
        ↓
Get Employee Details (Airtable)
        ↓
┌───────┴───────┐
↓               ↓
Check Dept    Get Manager → Update Record → Email Manager
↓
┌─────────┴─────────┐
↓                   ↓
Engineering       Marketing
↓                   ↓
Slack Invite      Slack Invite
↓                   ↓
Asana Tasks       Asana Tasks
(+Security)
↓                   ↓
Welcome Email     Welcome Email
↓
GitHub Invite
```

The workflow runs two parallel paths: department-specific onboarding (Slack, Asana, email, GitHub) and administrative updates (manager lookup, record update, manager notification).

## 🔧 Setup Instructions

### 1️⃣ Requirements

You'll need accounts for:
- [Airtable](https://airtable.com) (for employee and manager data)
- [Slack](https://slack.com) (Bot API for channel invites)
- [Asana](https://asana.com) (for task management)
- [Gmail](https://mail.google.com) (for welcome emails via OAuth)
- [GitHub](https://github.com) (for organization invites - Engineering only)

### 2️⃣ Import the Workflow

1. Download `Automated-Employee-Onboarding.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3️⃣ Configure Credentials

1. **Airtable**: Create a base "Automated Employee Onboarding Sequencer" with two tables:
   - **Employees**: `Name`, `Personal Email`, `Work Email`, `Department` (Engineering/Marketing), `Start Date`, `Slack User name`, `Manager` (linked)
   - **Managers**: `Name`, `Email`, `Department`
2. **Slack**: Create a bot with `channels:manage` and `groups:write` permissions
3. **Asana**: Connect via OAuth and set your workspace/project IDs
4. **Gmail**: Authorize OAuth2 for sending emails
5. **GitHub**: Connect via OAuth with organization admin permissions

### 4️⃣ Configure Slack Channels

Update the Slack channel IDs in the invite nodes:
- `Slack: Invite to #engineering`
- `Slack: Invite to #marketing`

### 5️⃣ Customize Onboarding Tasks

Edit the Asana nodes to customize:
- Task names and descriptions
- Subtask content (training videos, ID pickup instructions)
- Due dates (default: 7 days from start)

## 🧪 Example Use Cases

- **Startups**: Automate day-one setup so founders don't spend hours on admin
- **HR Teams**: Ensure every new hire gets the same consistent experience
- **Remote Companies**: Provision access across tools without manual coordination
- **Agencies**: Onboard contractors quickly with department-specific flows

## 💡 Pro Tips

- Add more departments by extending the Switch node with additional outputs
- Customize the HTML email templates in the Gmail nodes for your brand
- Add more tool integrations (Notion, Linear, 1Password) following the same pattern
- Use Airtable automations to pre-populate employee records from your HRIS
- Set up a "pre-boarding" flow for Day -1 prep (equipment ordering, account creation)

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with ❤️ using n8n, Airtable, Slack, Asana, Gmail, and GitHub
