# Agent Automation Lab

A multi-agent workspace that connects an Emergent web app to an n8n AI Agent workflow.

The application sends chat messages to an Emergent backend endpoint, which forwards them to a production n8n webhook. n8n handles the AI reasoning, memory, and tool execution, then returns the final assistant response to the web app.

## Features

- Live AI chat powered by n8n
- OpenAI chat model integration
- Conversation memory
- Gmail message sending
- Google Docs creation and updates
- Google Sheets row appending
- Google Calendar event creation
- Bing image search through SerpApi
- Mock fallback only when the production webhook request fails
- Production webhook integration through the Emergent backend

## Architecture

```text
User
  |
  v
Emergent Web App
  |
  v
POST /api/chat
  |
  v
Emergent Backend
  |
  | GET ?message=<url-encoded-message>
  v
n8n Production Webhook
  |
  v
AI Agent
  |
  +--> OpenAI Chat Model
  +--> Simple Memory
  +--> Gmail
  +--> Google Docs
  +--> Google Sheets
  +--> Google Calendar
  +--> SerpApi / Bing Images
  |
  v
Respond to Webhook
  |
  v
Emergent Backend
  |
  v
Web App
