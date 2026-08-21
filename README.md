# PERSONAIZER MCP Server

[![smithery badge](https://smithery.ai/badge/personaizer/personaizer-chat-and-rag)](https://smithery.ai/servers/personaizer/personaizer-chat-and-rag)

Create and operate AI chat personas for websites — over [MCP](https://modelcontextprotocol.io). Search a persona's knowledge base, chat with it, upload knowledge, and build brand-new personas from a URL, all from any MCP-compatible client (Claude Desktop, Claude Code, Cursor, etc.).

This repository is a directory listing for the hosted PERSONAIZER MCP server — the server itself is remote (Streamable HTTP), so there's no code to clone or run locally.

- **Registry entry:** `io.github.PersonAIzer/mcp` on the [official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=io.github.PersonAIzer/mcp)
- **Endpoint:** `https://sessions.personaizer.com/mcp`
- **Docs:** https://personaizer.com/developers/mcp
- **Sign up for a free API key:** https://personaizer.com

## Tools

| Tool | What it does | Key type |
|---|---|---|
| `search_knowledge` | Semantic search over a persona's knowledge base | persona secret key (`pa_...`) |
| `chat` | Send a message and get a reply from a persona | persona secret key, or account key + `persona_id` |
| `upload_knowledge_docs` | Add documents to a persona's knowledge base | persona secret key |
| `create_persona` | Build a new persona from a website URL | account key (`ak_...`) |
| `check_persona_status` | Poll a persona-creation job's progress | either key type |

## Quickstart

```bash
claude mcp add --transport http personaizer https://sessions.personaizer.com/mcp \
  --header "X-Api-Key: YOUR_API_KEY"
```

Get a persona secret key from a persona's Developer tab, or an account key from your [Account settings](https://personaizer.com/profile) — full walkthrough at [personaizer.com/developers/mcp](https://personaizer.com/developers/mcp).

## Authentication

Every request needs an `X-Api-Key` header:
- A **persona secret key** (`pa_...`) scopes `search_knowledge`, `chat`, and `upload_knowledge_docs` to one persona.
- An **account key** (`ak_...`) is account-wide — required for `create_persona`, and usable for `chat`/`check_persona_status` with an explicit `persona_id`.

## About PERSONAIZER

PERSONAIZER turns a website into a live AI persona your visitors can talk to — trained on your content, embeddable in minutes. Learn more at [personaizer.com](https://personaizer.com).
