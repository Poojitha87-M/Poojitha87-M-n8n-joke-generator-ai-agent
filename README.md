# Mood-Based Joke Generator – AI Agent Workflow (n8n)

A small AI automation built with [n8n](https://n8n.io). Send a POST request with a mood, and an AI Agent powered by an OpenAI chat model (`gpt-5-mini`) generates one joke to match it and returns it as a JSON response.

This project was built as a proof of concept to practise n8n workflow automation, AI Agent nodes, prompt writing and LLM integration through APIs.

## How it works

```
Webhook (POST)  →  AI Agent (OpenAI Chat Model)  →  Respond to Webhook
```

| Node | Purpose |
|------|---------|
| **Webhook** | Receives the POST request and reads the `mood` field from the JSON body |
| **AI Agent** | Uses a prompt that asks for exactly one funny joke for that mood, with no advice, options or explanations |
| **OpenAI Chat Model** | The LLM (`gpt-5-mini`) that powers the AI Agent |
| **Respond to Webhook** | Returns the result to the caller as JSON: `{ "joke": "..." }` |

## Tech stack

- n8n (workflow automation, AI Agent node)
- OpenAI Chat Model (`gpt-5-mini`) via API
- Webhooks, JSON

## Setup

1. Install or open n8n (self-hosted, Docker, or n8n Cloud).
2. Import the workflow: **Workflows → Import from File** and select the `.json` file in this repository.
3. Open the **OpenAI Chat Model** node and connect your own OpenAI credentials. No API keys are stored in this repository.
4. Click **Execute workflow** to test with the test webhook URL, or activate the workflow to use the production webhook URL.

## Usage

Send a POST request to your webhook URL with a `mood`:

```bash
curl -X POST "<YOUR_N8N_WEBHOOK_URL>" \
  -H "Content-Type: application/json" \
  -d '{"mood": "stressed"}'
```

Example response format:

```json
{ "joke": "<one joke matching the mood>" }
```

## Screenshot

![n8n workflow](Screenshot%202026-11-22%20104249.png)

## What I learned

- Building an end-to-end workflow in n8n with a webhook trigger and a JSON response node
- Passing request data (`mood`) into an AI Agent prompt and constraining the output to a single joke
- Connecting an LLM to an AI Agent node through an OpenAI chat model
- Exposing an automation as an API endpoint that other tools can call

## Possible improvements

- Add validation and error handling for a missing or empty `mood`
- Add memory so the agent remembers earlier requests
- Add tools, or send the joke to Telegram, email or Slack

## Author

**Makkapati Poojitha** – [LinkedIn](https://www.linkedin.com/in/poojitha985/) | [GitHub](https://github.com/Poojitha87-M)
