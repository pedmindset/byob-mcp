<p align="center"><img src="assets/logo.png" width="128" alt="BYOB"></p>

# BYOB MCP connector

Connect Grok, Grok Bot, Cursor, Claude, ChatGPT or any MCP-capable assistant to **BYOB** ([byobgh.com](https://byobgh.com)), Ghana's phone and electronics retail, sales-agent and delivery platform, built by PED Solution Studio.

This repository contains configuration only, with no executable code. It points your client at BYOB's hosted, remote MCP server:

```
https://byobgh.com/mcp/byob
```

## What it does

Once you sign in, your assistant can work with BYOB on your behalf, for example:

- **Sales agents:** search the catalogue and stock, check prices, create and follow orders, view commissions.
- **Riders:** see assigned deliveries, update delivery status, confirm cash-on-delivery collections.
- **Warehouse staff:** pick, pack and dispatch orders, handle returns and stock checks.
- **Admins:** order, refund and reporting tools. Sensitive actions (such as refunds above a set limit) require approval by a second admin.

## Role-based access

Tools follow your BYOB role. You only see and can call the tools your account is allowed to use, and every action is checked server-side and logged against your account.

## Sign-in (OAuth 2.1)

No API keys. The server uses OAuth 2.1 with PKCE and dynamic client registration (discovery at `https://byobgh.com/.well-known/oauth-authorization-server`). The first time you use it, your client opens a BYOB sign-in page; approve access with your normal BYOB login. You can revoke connected apps at any time from your BYOB account.

## Setup

**Grok / Grok Bot:** go to grok.com/connectors → New Connector → Custom, enter `https://byobgh.com/mcp/byob`, and sign in. Or install the `byob` plugin from the marketplace.

**Cursor:** install the BYOB plugin, or add this to `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{ "mcpServers": { "byob": { "url": "https://byobgh.com/mcp/byob" } } }
```

Then open Settings → MCP and click **Connect** to sign in.

**Claude:** Settings → Connectors → Add custom connector → `https://byobgh.com/mcp/byob`.

**ChatGPT:** Settings → Apps & Connectors (Developer mode) → Create → `https://byobgh.com/mcp/byob`, authentication OAuth.

**Other clients:** use the Streamable HTTP URL above with OAuth.

## Network endpoints and credentials

- Calls only `https://byobgh.com` (MCP endpoint and OAuth endpoints).
- Needs no local credentials, environment variables or tokens. Access tokens are issued by BYOB through OAuth and stored by your client.
- No hooks, scripts, skills or telemetry are shipped in this repo.

## Privacy, terms and support

- Privacy policy: https://byobgh.com/privacy
- Terms: https://byobgh.com/terms
- Support: support@byobgh.com · https://byobgh.com/support

## License

MIT © PED Solution Studio. See [LICENSE](LICENSE).
