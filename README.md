# SetLatch MCP server

<img src="https://setlatch.com/icon-512.png" alt="SetLatch" width="96" align="right">

Hosted MCP server for [SetLatch](https://setlatch.com): privacy request (DSAR) software for web agencies and the sites they run. Handle GDPR, UK GDPR and US state privacy requests (CCPA and others) for every client site from your AI assistant.

**Endpoint:** `https://setlatch.com/mcp` (Streamable HTTP, OAuth 2.1 sign-in)
**Docs:** https://setlatch.com/docs/ai-assistants
**Official MCP Registry:** `com.setlatch/setlatch`

This repository only describes the hosted server. There is nothing to install or run: SetLatch is a hosted service and its source is not public.

## What it can do

- See which requests are due across all your sites, and read any request in full
- Look the requester up in the site's connected apps (Mailchimp, Stripe, Shopify, WooCommerce, HubSpot, Klaviyo, Gmail, Resend, Cloudflare, signed webhooks) and record what each one holds. Look-ups are read-only at the vendor.
- Log requests that arrived by email, phone or post, and record calls and letters
- Mark tasks done or "nothing held", with what the requester will be told
- Keep each site's data map current
- Read the tamper-evident audit trail

**What it cannot do:** delete or change anything in a connected app, approve a deletion, or write to a requester. Those always stay a person's click in the SetLatch dashboard. The only email it can trigger is SetLatch's standard identity-check link when it logs a new request (and that can be turned off per request). Everything the assistant does is recorded in the audit trail under the person who connected it.

## Tools

| Tool | What it does |
|---|---|
| `list_sites` | Sites you can work on |
| `list_requests` | Requests on a site, by status and deadline |
| `get_request` | One request in full: tasks, deadlines, messages |
| `get_data_map` | The site's systems that hold personal data |
| `get_audit_trail` | Audit events |
| `list_connections` | Which apps are connected to the site |
| `look_up_requester` | Ask connected apps whether they hold the requester |
| `create_request` | Log a request received outside the web form |
| `log_correspondence` | Record a call, email or letter |
| `add_data_map_system` | Add a system to the data map |
| `add_missing_tasks` | Give tasks to systems added after verification |
| `update_request_status` | Move a request on (e.g. verified, rejected) |
| `update_task` | Mark a task done or nothing held, with notes |
| `update_data_map_system` | Edit a data map system |

## Connect

**Claude.ai / Claude Desktop:** Settings → Connectors → Add custom connector → `https://setlatch.com/mcp`

**Claude Code:**
```bash
claude mcp add --transport http setlatch https://setlatch.com/mcp
```

**Cursor, VS Code and other `mcp.json` clients:**
```json
{ "mcpServers": { "setlatch": { "url": "https://setlatch.com/mcp" } } }
```

Your client opens a browser to sign in. You choose which sites the assistant may use, whether it may change anything, and whether it may run look-ups. Clients without OAuth can send a personal token (`Authorization: Bearer slt_…`) made in SetLatch under AI assistants.

Requires a SetLatch account (Single site or Agency plan, 14-day free trial).

## Support

support@setlatch.com · [Privacy policy](https://setlatch.com/privacy) · [Terms](https://setlatch.com/terms) · [Security](https://setlatch.com/security)

© SetLatch Pty Ltd
