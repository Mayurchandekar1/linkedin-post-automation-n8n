# LinkedIn Post Automation Pipeline

An agentic workflow that fully automates LinkedIn content posting
using n8n running on Docker.

## What it does
1. Reads a post topic from Google Sheets (status = pending)
2. Sends topic to an AI Agent (OpenRouter LLM) to write the post
3. Auto-publishes the generated post to LinkedIn
4. Updates the sheet row — sets status to "posted" + logs the date

## Workflow diagram
![Workflow](Screenshot_2026-03-15_112036.png)

## Tech Stack
- n8n (workflow automation, self-hosted via Docker)
- OpenRouter API (LLM / AI Agent — GPT model)
- Google Sheets API (topic queue + status tracking)
- LinkedIn API (auto-publishing)
- Docker (local containerised deployment)

## How to run

### 1. Start n8n with Docker
```bash
docker-compose up -d
```
Then open: http://localhost:5678

### 2. Add your credentials in n8n
- OpenRouter API key
- Google Sheets OAuth
- LinkedIn OAuth

### 3. Import the workflow
Go to n8n → Workflows → Import → select `workflow_clean.json`

### 4. Set up your Google Sheet
Columns needed: `topic` | `status` | `post` | `posted_date`
Set status = `pending` for any row you want posted.

### 5. Run it
Click Execute — or enable the Schedule Trigger for weekly auto-posting.
