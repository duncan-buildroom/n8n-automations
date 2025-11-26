# Build Room Automations

### Client Acquisition, Content Engine, and Monetization Workflows for n8n

This repository contains the exact n8n workflows used inside The Build Room ecosystem to automate client acquisition, content production, and revenue operations for AI/automation agencies.

These workflows are designed for aspiring and active AI agency founders who want to launch, scale, and automate faster — without needing to be technical.

---

## What This Repo Includes

### 1. Client Acquisition Workflows

Automations that help agencies attract and close clients using The Build Room methodology.
Examples:

* LinkedIn client pipeline sync
* Lead capture → nurture segmentation
* Discovery call booking automations
* Lead scoring and qualification logic
* High-intent DM triggers

### 2. Content System Workflows

Automations that turn long-form content into a multi-channel publishing engine.
Examples:

* YouTube → LinkedIn → TikTok repurposing pipelines
* Content idea generation + scheduling
* Auto-export, cleaning, and clipping
* Metrics tracking for platform performance

### 3. Monetization & Delivery Workflows

Systems that support revenue operations, community management, and client delivery.
Examples:

* Payment events → onboarding automation
* Community access provisioning
* Task/project creation for client builds
* Retention and renewal sequences
* KPI dashboards via Airtable/Sheets

---

## Why These Workflows Exist

Most new AI agency founders get stuck in three areas:

1. Getting consistent leads
2. Posting consistent content
3. Delivering client work quickly and profitably

These n8n automations remove friction across all three — compressing time, reducing workload, and increasing perceived likelihood of success.
They are built using principles from:

* Funnel and nurture frameworks for AI agencies 
* Persona-based acquisition and segmentation strategy 
* Vibe Marketing content design principles 
* Hormozi’s Grand Slam Offer and Core Four lead acquisition frameworks

---

## How to Use This Repo

### 1. Import Workflows

Each workflow is exported as an `.json` file.
Inside n8n:
Settings → Import → Upload the workflow file.

### 2. Configure Credentials

Most workflows use:

* Notion
* Airtable
* GHL or ConvertKit
* LinkedIn API or PhantomBuster
* OpenAI API
* Google Sheets
* Slack/Discord
  Credential placeholders are clearly labeled inside each file.

### 3. Customize to Your Offer

Each workflow includes notes explaining:

* Where to insert your offers
* Recommended lead magnets
* Segmentation fields
* Optional upsell paths
* Metrics to track

### 4. Deploy to Production

Run via:

* n8n Cloud
* Self-hosted instance (Docker recommended)
* Trigger via cron or webhook depending on the workflow

---

## Folder Structure

```
/client-acquisition
  linkedin-pipeline.json
  lead-intake.json
  nurture-logic.json

/content-engine
  youtube-to-linkedin.json
  repurpose-pipeline.json
  content-calendar-generator.json

/monetization
  onboarding-automation.json
  renewal-retention.json
  payment-event-router.json

/docs
  diagrams
  instructions
```

---

## ICP Fit

These workflows are built for:

* Aspiring AI agency founders
* Displaced workers starting agencies
* Career changers transitioning into automation
* Stalled professionals seeking higher-value skills
* Non-technical newcomers needing fast wins

The workflows intentionally reduce time delay, effort, and failure points while increasing the likelihood of acquiring clients and generating income.

---

## License

MIT License.
Use freely. Modify freely. Build freely.

---

## Contribute

If you want to add new workflows, improve documentation, or contribute features, open a pull request.

---

## Need Help Implementing?

Join The Build Room community FOR FREE for templates, training, automations, and weekly support.
Or apply for the 4-week 1:1 sprint if you want everything implemented fast.

https://www.skool.com/buildroom

Just tell me which.

