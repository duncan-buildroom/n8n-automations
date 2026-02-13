# 🔥 The "Pitch Deck" Roaster

> Upload your pitch deck and get it brutally critiqued with red-pen annotations like a cynical VC.

One of the systems I teach inside [The Build Room](https://www.skool.com/buildroom) to help you get more leads using AI.

## Video Walkthrough

[Link here] is a FULL DEMO with output examples and a step by step video walkthrough of how to setup the automation.

## Overview

The Pitch Deck Roaster is an n8n automation that automatically:

- Accepts a PDF pitch deck upload
- Analyzes the entire deck using Gemini AI as a cynical VC
- Generates a brutal text critique with page-by-page annotations
- Converts the PDF into individual slide images
- Visually marks up each slide with red-pen corrections
- Circles problems, crosses out bad content, writes critique directly on slides
- Reassembles everything into an annotated PDF for download

It's designed for founders, pitch coaches, and anyone who wants honest (brutal) feedback on their investor presentations.

> Free AI tutorials: Learn how to build automations like this on [@duncanrogoff](https://youtube.com/@duncanrogoff)

## Features

| Feature | Description |
|---------|-------------|
| 📄 **PDF Upload** | Drag and drop your pitch deck |
| 🎭 **Cynical VC Persona** | High-stakes Silicon Valley critique style |
| ✍️ **Text Analysis** | Overall feedback + page-by-page annotations |
| 🖼️ **Slide Extraction** | Converts PDF pages to individual images |
| 🔴 **Red Pen Markup** | Visual circles, X marks, and handwritten notes |
| 📑 **PDF Reassembly** | Download a fully annotated deck |

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                 PHASE 1: INGESTION & TEXT ANALYSIS                  │
├─────────────────────────────────────────────────────────────────────┤
│  Form Trigger: Upload Pitch Deck (PDF)                              │
│                    ↓                                                │
│  Gemini: Upload File → Analyze Document                             │
│                    ↓                                                │
│  Gemini: Generate Text Critique                                     │
│  • Cynical VC persona                                               │
│  • Humiliating headline for the deck                                │
│  • Overall brutal feedback (2-3 sentences)                          │
│  • Page-by-page "Fix This" instructions                             │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 2: PDF DECONSTRUCTION                        │
├─────────────────────────────────────────────────────────────────────┤
│  Drive: Backup Original PDF                                         │
│                    ↓                                                │
│  PDF.co: Convert PDF to JPG (async)                                 │
│                    ↓                                                │
│  Wait → PDF.co: Get JPG URLs                                        │
│                    ↓                                                │
│  Format: Individual slide images                                    │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                  PHASE 3: THE "RED PEN" LOOP                        │
├─────────────────────────────────────────────────────────────────────┤
│  Merge: Roast Text + Slide Images                                   │
│                    ↓                                                │
│  Loop: Per Slide                                                    │
│                    ↓                                                │
│  HTTP: Fetch Image → Gemini: Visual Red Pen                         │
│  • Matches slide to page-specific critique                          │
│  • Draws red circles around problems                                │
│  • Crosses out bad content with X marks                             │
│  • Writes handwritten-style critique                                │
│  • Adds red question mark if no match found                         │
│                    ↓                                                │
│  Drive: Upload Annotated Slide                                      │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│                   PHASE 4: REASSEMBLY & OUTPUT                      │
├─────────────────────────────────────────────────────────────────────┤
│  Aggregate: All Annotated Images                                    │
│                    ↓                                                │
│  PDF.co: Merge Images to PDF                                        │
│                    ↓                                                │
│  Drive: Upload Final PDF                                            │
│                    ↓                                                │
│  Form Response: Redirect to Download Link                           │
└─────────────────────────────────────────────────────────────────────┘
```

## The Roast Output

### Text Critique Format:
```json
{
  "title": "[Punchy, humiliating headline]",
  "body": "[Overall feedback + PAGE-BY-PAGE ANNOTATIONS: Page 3: Delete this graph...]"
}
```

### Visual Annotations:
- **Red Circles**: Around confusing charts, vague titles
- **Red X Marks**: Crossing out bad content
- **Handwritten Notes**: Punchy critique summaries
- **Question Marks**: For unmatched slides

## Setup Instructions

### 1. Requirements

You'll need accounts for:
- [Google AI Studio](https://makersuite.google.com) (Gemini 3 Pro + Gemini 3 Pro Image Preview)
- [PDF.co](https://pdf.co) (PDF to JPG conversion and merging)
- [Google Drive](https://drive.google.com) (file storage)

### 2. Import the Workflow

1. Download `workflow.json` from this folder
2. In n8n, go to **Workflows → Import from File**
3. Select the downloaded JSON file

### 3. Set Up Google Drive

1. Create a folder for Pitch Deck Roaster outputs
2. Update the folder ID in the Drive nodes

### 4. Configure Credentials

1. **Google Gemini**: Add your API key for analysis and visual editing
2. **PDF.co**: Add your API key for PDF operations
3. **Google Drive**: Authorize OAuth2 for file operations

## Example Use Cases

- **Founders**: Get brutal feedback before pitching real VCs
- **Pitch Coaches**: Generate visual feedback for clients
- **Accelerators**: Provide scalable deck reviews
- **Content Creators**: Create entertaining "roast" content

## Pro Tips

- The VC persona is intentionally cynical - it's meant to surface weak spots
- Every slide gets matched to specific feedback in the text critique
- Red pen annotations are handwritten-style for authenticity
- The original PDF is backed up before processing
- Download link is provided immediately after processing
- Use this as a first pass before polishing your deck

---

## 🚀 Want to Build a Profitable Personal Brand Using AI?

Join **The Build Room** — the fastest way to build a highly profitable personal brand using AI.

Get your first leads in 14 days and 1,500+ real followers in under 49 days. Guaranteed.

[→ Join The Build Room](https://www.skool.com/buildroom)

---

Built with n8n, Google Gemini 3 Pro, Gemini 3 Pro Image Preview, PDF.co, and Google Drive
