I used AI to help me build this project to debug, accelerate and implement the implementation of it.

## 1. Architectural Strategy
Context: I provided the Cloudflare "Optional Assignment" requirements (Llama 3.3, Workers, Durable Objects, State, User Input).
Prompt: "Implement and open a pull request for the first issue I have assigned to me... I'm using a self-hosted git instance, and the implementation should be in JavaScript."
AI Response: The AI looked at the requirements and recommended using the Cloudflare Agents SDK starter template (`agents-starter`) as the most efficient path

## 2. Environment Debugging (Node.js)
Context: I encountered an error when trying to initialize the project. (forgot I didnt have Node.js installed on my computer)
Prompt: `npm : The term 'npm' is not recognized as the name of a cmdlet, function, script file, or operable program.`
AI Response: Diagnosed that Node.js was not installed on the Windows environment and provided step-by-step instructions to install the LTS version and restart the PowerShell session.

## 3. Project Scaffolding & Naming Conventions
Context: I set the repository name to `cf_ai_agent` as the assignment required, but the `create-cloudflare` CLI rejected it.
Prompt: `ERROR Project names must only contain lowercase characters, numbers, and dashes.`
AI Response: Provided a workaround:
1. Initialize the project using dashes (`cf-ai-agent`) to satisfy the CLI.
2. Manually rename the directory to `cf_ai_agent` immediately after creation to satisfy the assignment requirement.

## 4. Implementation (Switching to Llama 3.3)
Context: The starter kit defaults to OpenAI, but the assignment required Cloudflare Workers AI.
Prompt: Help me convert this to LLama 3.3.
AI Response: Identified that the code was still using `@ai-sdk/openai`. Provided the specific TypeScript code for `src/server.ts` to:
1. Import `workers-ai-provider`.
2. Initialize the model using the `@cf/meta/llama-3.3-70b-instruct-fp8-fast` ID.
3. Bind the model to the `this.env.AI` environment variable.

## 5. Runtime Debugging
Context: The application crashed upon sending the first message.
Prompt: `Error on server: Error: jsonSchema not initialized. at MCPClientManager.getAITools...` (the error I got)
AI Response: Diagnosed that the code was attempting to load Model Context Protocol (MCP) tools without a connected MCP server. Provided a fix to remove `...this.mcp.getAITools()` from the tools definition in `src/server.ts`, resolving the crash.

## 6. Prompting Help
Context: The bot was being stubborn and not helping.
Prompt: How can I make the bot not say `I am not able to complete this task as it falls outside of the scope of the functions I have been given.`
AI Response: Told me to change bot prompt to whats implemented.

