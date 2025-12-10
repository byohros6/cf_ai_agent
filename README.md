# Cloudflare AI Agent (cf_ai_agent)

This is a context-aware AI chat agent built on Cloudflare Workers, Durable Objects, and Workers AI.

## Project Requirements Met
- **LLM**: Uses **Llama 3.3** (`@cf/meta/llama-3.3-70b-instruct-fp8-fast`) via Workers AI.
- **Workflow / Coordination**: Uses **Durable Objects** to manage the agent lifecycle and `agents` SDK for orchestration.
- **User Input**: React frontend with WebSocket connection for real-time chat.
- **Memory / State**: Chat history is persisted automatically in the Durable Object's SQL storage.

## Setup & Running

1. **Install Dependencies**:
   ```bash
   npm install