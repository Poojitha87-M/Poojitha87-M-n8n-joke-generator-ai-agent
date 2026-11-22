# Joke Generator – AI Agent Workflow (n8n)

A small AI automation built with [n8n](https://n8n.io). It exposes a webhook endpoint: send it a POST request and an AI Agent, powered by an OpenAI chat model, generates a joke and returns it as the response.

This project was built as a proof of concept to practise n8n workflow automation, AI Agent nodes and LLM integration through APIs.

## How it works

```
Webhook (POST)  →  AI Agent (OpenAI Chat Model)  →  Respond to Webhook
```

| Node | Purpose |
|------|---------|
| **Webhook** | Receives the incoming POST request and starts the workflow |
| **AI Agent** | Takes the request and generates a joke using the connected chat model |
| **OpenAI Chat Model** | The LLM that powers the AI Agent |
| **Respond to Webhook** | Sends the generated joke back to the caller |

## Tech stack

- n8n (workflow automation, AI Agent node)
- OpenAI Chat Model (via API)
- Webhooks / HTTP

## Setup

1. Install or open n8n (self-hosted, Docker, or n8n Cloud).
2. Import the workflow: **Workflows → Import from File** and select the workflow `.json` file from this repository.
3. Open the **OpenAI Chat Model** node and add your own OpenAI API credentials. No keys are stored in this repository.
4. Click **Execute workflow** to test, or activate the workflow to use the production webhook URL.

## Usage

Send a POST request to your webhook URL:

```bash
curl -X POST "<YOUR_N8N_WEBHOOK_URL>" \
  -H "Content-Type: application/json" \
  -d '{"message": "Tell me a joke"}'
```

The workflow responds with the generated joke.



## What I learned

- Building an end-to-end workflow in n8n using a webhook trigger and a response node
- Connecting an LLM to an AI Agent node through an OpenAI chat model
- Exposing an automation as an API endpoint that other tools can call

## Possible improvements

- Add memory so the agent remembers earlier requests
- Let the caller choose a joke topic or tone
- Add tools or send the joke to Telegram, email or Slack
- Add error handling for failed or empty responses

## Author

**Makkapati Poojitha** – [LinkedIn](https://www.linkedin.com/in/poojitha985/) | [GitHub](https://github.com/Poojitha87-M)
