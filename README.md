# AI Lead Qualification Agent

An automated lead qualification system built with **n8n** and **Claude (Anthropic)** that evaluates incoming leads in real time, scores them based on business-defined criteria, and routes qualified leads for immediate follow-up — without any manual review.

## What It Does

When a potential client submits an inquiry through a form, this workflow automatically:

1. **Captures the lead's details** — name, email, project needs, and budget — via a connected intake form
2. **Analyzes the lead using AI** — Claude evaluates the submission against four qualification criteria: budget clarity, project specificity, urgency, and service fit
3. **Assigns a score and category** — each lead is rated 1–10 and labeled Hot, Warm, or Cold, along with a clear explanation of the reasoning
4. **Filters and routes automatically** — Hot leads are immediately logged to a dedicated spreadsheet with a recommended next action, so no promising lead is missed or delayed
5. **Runs continuously** — the entire process is triggered automatically on new form submissions, requiring zero manual intervention

## Why This Matters

Manually reading and evaluating every inbound inquiry is slow and inconsistent. This agent applies the same qualification logic every time, at any hour, and surfaces only the leads worth immediate attention.

## Tech Stack

- **n8n** — workflow automation and orchestration
- **Claude (Anthropic)** — natural language reasoning and lead scoring
- **Google Forms** — lead intake
- **Google Sheets** — response storage and qualified lead logging

## How It Works (Architecture)

Google Form Submission → Google Sheets (stores raw response) → n8n Trigger (detects new row) → AI Agent (Claude scores and reasons about the lead) → Conditional Filter (Hot leads only) → Google Sheets (logs qualified lead + recommended action)

## Example Output

```json
{
  "name": "Sarah",
  "score": 9,
  "category": "Hot",
  "reason": "Clear budget, specific deliverable, immediate urgency, and direct fit with services offered.",
  "suggested_next_step": "Respond immediately with a proposal and schedule an onboarding call."
}
```

## Setup

1. Import `workflow.json` into your n8n instance
2. Connect your own Google account (Sheets/Forms) and an Anthropic API credential
3. Update the sheet/document references to point to your own intake form's response sheet
4. Activate the workflow

## About This Project

This project was built as a hands-on exploration of AI agent design — combining large language model reasoning with automation tooling to make real judgment calls, not just fixed if/then rules.
