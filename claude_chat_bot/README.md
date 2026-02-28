# Claude Chat Bot — AI Assistant Web Application for Odoo

A pre-built AI chat assistant powered by the Anthropic Claude API, running as an MCP Studio web application inside Odoo. Provides a shared Claude interface for your team — 100 users, one API key, full conversation history.

## Overview

This is an exportable web application built with the **Odoo MCP Studio** webapp framework. It provides a ChatGPT/Claude-style chat interface that runs directly from your Odoo instance, with features including:

- **Multi-model support** — Switch between Claude Opus, Sonnet, and Haiku
- **Conversation management** — Multiple chat threads with persistent history
- **Tool integration** — Web search, code execution, and MCP tools (connect back to your own Odoo instance)
- **File uploads with OCR** — Upload images, PDFs, and documents via the Anthropic Files API with built-in OCR for text extraction
- **Theme system** — Multiple color themes (Claude, Midnight, Ocean, Forest, Sunset)
- **Mobile responsive** — Works on desktop and mobile browsers
- **Progressive Web App** — Installable on mobile and desktop for a native app experience
- **Shared usage** — All users share a single Anthropic API key managed by the administrator
- **Prompt caching** — Automatic caching of conversation prefixes for faster responses and reduced API costs
- **Context compaction** — Server-side summarization of long conversations to stay within context limits
- **Context editing** — Automatic clearing of old tool results and thinking blocks to keep context focused

### Architecture

```
┌──────────────────────────────────────────────────┐
│           User's Browser (React 19 SPA)          │
│                                                  │
│  Chat UI → POST /mcp/webapp/{id}/api/chat        │
│         → POST /mcp/webapp/{id}/api/files/upload  │
│         → GET  /mcp/webapp/{id}/api/files         │
└──────────────────────────────────────────────────┘
                        │
                        ▼
┌──────────────────────────────────────────────────┐
│              Odoo (MCP Studio Webapp)            │
│                                                  │
│  Endpoint handler (safe_eval sandbox)            │
│  → Reads API key from mcp.api.key model          │
│  → Proxies request to Anthropic Messages API     │
│  → Returns streamed response to frontend         │
└──────────────────────────────────────────────────┘
                        │
                        ▼
┌──────────────────────────────────────────────────┐
│            Anthropic Messages API                │
│                                                  │
│  Claude Opus / Sonnet / Haiku                    │
│  + Web Search + Code Execution + MCP Tools       │
│  + Prompt Caching + Compaction + Context Editing  │
└──────────────────────────────────────────────────┘
```

### Context Management (Opus 4.6 / Sonnet 4.6)

The application includes a layered context management strategy that activates automatically for supported models:

1. **Prompt Caching** — Conversation prefixes and system prompts are cached using `cache_control: {"type": "ephemeral"}`. On turn 2+, cached tokens cost only 10% of normal input price, significantly reducing costs for multi-turn conversations. Cache hits are displayed in the usage footer (e.g., "⚡12000 cached").

2. **Thinking Block Clearing** (at any context size) — When extended thinking is enabled, old thinking blocks are automatically cleared, keeping only the last 2 assistant turns. This prevents thinking content from consuming context space.

3. **Tool Result Clearing** (at 50k+ input tokens) — Old tool results (MCP calls, web search results, code execution output) that Claude has already processed are replaced with placeholders. The 5 most recent tool interactions are preserved.

4. **Server-Side Compaction** (at 100k+ input tokens) — The entire conversation is automatically summarized into a compact summary block. Earlier messages are dropped and replaced with the summary, allowing conversations to continue indefinitely. A visual indicator ("↻ Context compacted") appears in the chat when this occurs.

These features use the `compact-2026-01-12` and `context-management-2025-06-27` beta APIs. Models that don't support these features (e.g., Haiku) gracefully fall back to standard behavior.

### Model-Specific Tool Versions

Opus 4.6 and Sonnet 4.6 automatically use the latest tool versions (`web_search_20260209`, `web_fetch_20260209`), while other models fall back to stable versions (`web_search_20250305`, `web_fetch_20250910`).

---

## Requirements

- **Odoo 19** with **MCP Studio** module installed (odoo_remote_mcp)
- **Anthropic API key** — Get one from [console.anthropic.com](https://console.anthropic.com)
- **(Optional) MCP API key** — For connecting Claude back to your Odoo instance via MCP tools

---

## Installation

### Step 1: Import the Web Application

1. Download the `Claude_Chat.csv` file from this folder
2. In Odoo, navigate to **MCP Server → Web Applications**
3. Click **Import records** (star icon in list view header)
4. Upload `Claude_Chat.csv` and click **Import**
5. The web application will appear in your Web Applications list

### Step 2: Configure API Keys

1. Navigate to **MCP Server → API Keys**
2. Create two API key records:

**Required — Anthropic API Key:**

| Field | Value |
|-------|-------|
| Name | `anthropic-api` |
| API Key | Your Anthropic API key (e.g., `sk-ant-...`) |
| User | Any MCP user (used for audit logging) |

**Optional — MCP Connector Key (for Odoo tool access):**

| Field | Value |
|-------|-------|
| Name | `claude-bot` |
| API Key | Generate one using the **Generate** button |
| User | The Odoo user whose permissions Claude should operate with |
| Scope | `odoo.read odoo.write odoo.execute offline_access` (default) |

The `claude-bot` key allows Claude to call back into your Odoo instance using MCP tools (search records, create records, etc.). The permissions are tied to the **User** configured on the key — ensure that user has appropriate (minimal) tool allowlists in MCP Configuration.

### Step 3: Open the Application

1. Go to **MCP Server → Web Applications**
2. Find "Claude Chat" in the list
3. Click **Open App** (or navigate to the webapp URL directly)

---

## Configuration

### API Keys

API keys are stored in the `mcp.api.key` model, which is restricted to MCP Administrators. Keys are never exposed to end users — the endpoint handler reads them server-side by name.

| Name | Purpose | Required |
|------|---------|----------|
| `anthropic-api` | Authenticates requests to the Anthropic Messages API | Yes |
| `claude-bot` | Bearer token for MCP tool calls back to Odoo | Optional |

### Access Control

Configure who can access the chat bot via the webapp's **Sharing** tab:
- **Internal users** — Add specific users or user groups
- **Portal users** — Add the Portal group for customer-facing use
- **Public** — Add the Public group for open access (not recommended without rate limiting)

### Tool Toggles

The chat interface includes three tool toggles:
- **Web** — Enables web search and web fetch (Claude can search the internet)
- **Code** — Enables code execution (Claude can run Python code in a sandboxed container — generate Word documents, PowerPoint presentations, Excel spreadsheets, PDFs, charts, data analysis, and more with downloadable output files)
- **MCP** — Enables MCP tools (Claude can interact with your Odoo instance)

Note: On Opus 4.6 and Sonnet 4.6, when both Web and Code are enabled, code execution is auto-injected by the newer web tool versions, so only one code execution tool instance is registered.

---

## Disclaimer

**This is a showcase/demo application.** It demonstrates what's possible with the MCP Studio webapp framework and the Anthropic API. Please be aware of the following limitations:

### Security Considerations

- **No built-in rate limiting** — There is no application-level rate limiting. See [Rate Limiting with Workspaces](#rate-limiting-with-workspaces) below for the recommended approach using Anthropic Workspaces.
- **Shared API key** — By default all users share the same Anthropic API key and usage costs are pooled.
- **No per-user billing** — There is no built-in mechanism to track or limit per-user API spend.
- **File namespace** — Uploaded files via the Anthropic Files API are visible to all users of the application (files are stored in a shared Anthropic organization namespace).
- **User-controlled system prompt** — The system prompt and model selection are user-configurable. For a more locked-down deployment, modify the endpoint handler to enforce defaults.
- **MCP tool access** — When MCP tools are enabled, Claude operates with the permissions of the MCP API key owner. Ensure the associated Odoo user has appropriate (minimal) permissions and tool allowlists.

### Recommended Usage

- **Internal teams** — Best suited for trusted internal users where API costs are acceptable
- **Development/staging** — Great for prototyping AI-powered workflows before building a production integration
- **Demonstrations** — Showcase AI capabilities to stakeholders

### Rate Limiting with Workspaces

The recommended approach for enforcing rate limits is to use **Anthropic Workspaces**. Each workspace gets its own API key and can have independent rate limits (requests per minute, tokens per minute, etc.) configured in the Anthropic Console.

See: [Setting lower limits for Workspaces](https://platform.claude.com/docs/en/api/rate-limits#setting-lower-limits-for-workspaces)

**Setup:**

1. In the [Anthropic Console](https://console.anthropic.com), create a separate **Workspace** for each team or usage tier
2. Generate an API key in each workspace and configure its rate limits
3. In Odoo, duplicate the Claude Chat webapp (one copy per workspace)
4. For each copy, create an `mcp.api.key` record with a unique name (e.g., `anthropic-api-sales`, `anthropic-api-support`)
5. Update the API key lookup name in the **Send Chat Message** endpoint handler — change the `anthropic-api` reference on this line:

   ```python
   api_rec = env['mcp.api.key'].sudo().search([('name', '=', 'anthropic-api')], limit=1)
   ```

   For example, change `'anthropic-api'` to `'anthropic-api-sales'` for the sales team's copy.

6. Configure each webapp's **Sharing** tab to restrict access to the appropriate user group

This same pattern is useful for **MCP tool access control**. The `claude-bot` API key determines which MCP tools Claude can access — the tools available are governed by the **User** configured on that key record and their MCP tool allowlist. By creating separate webapp copies with different `claude-bot` keys (each tied to a different Odoo user with different permissions), you can give developers full read/write MCP access while restricting support staff to read-only operations, for example. Update the key lookup in the endpoint handler the same way:

   ```python
   mcp_rec = env['mcp.api.key'].sudo().search([('name', '=', 'claude-bot')], limit=1)
   ```

   Change `'claude-bot'` to e.g., `'claude-bot-sales'` or `'claude-bot-support'` to match the key name for that team's copy.

This gives you per-team rate limiting, spend isolation, MCP tool restrictions, and usage tracking — all enforced at the API level.

### Extending the Concept

This application is a starting point. The same architecture can be adapted for:
- **E-commerce chatbots** — Customer-facing assistants with access to product catalogs and order data
- **Support agents** — Helpdesk bots connected to ticket systems via MCP
- **Data analysis tools** — Internal dashboards with natural language querying
- **Custom AI agents** — Any domain-specific assistant powered by Claude + Odoo data

---

## Customization

Since this is an MCP Studio web application, everything is editable directly in Odoo:

- **Frontend (React)** — Edit the page `component_code` in the webapp form view
- **Backend (Python)** — Edit endpoint `handler_code` for API proxy logic
- **Styling** — Modify the theme system or Tailwind classes in the component code
- **Tools** — Add or remove tool definitions in the endpoint handler

You can also use an AI agent connected via MCP to modify the application itself — "vibecode" your AI assistant.

---

## License

This web application export is provided as-is under the same license as the MCP Studio module (OPL-1). See the main module's LICENSE file for details.
