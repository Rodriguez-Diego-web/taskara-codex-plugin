# Taskara for Codex

The official public Codex plugin for [Taskara](https://taskara.de), the back-office platform for cleaning and facility-service teams.

Taskara connects to Codex through the production MCP endpoint at `https://taskara.de/api/mcp`. Authentication uses Taskara OAuth with PKCE. Your password stays on Taskara and is never shared with Codex.

[Watch the verified MCP demo](plugins/taskara/assets/taskara-plugin-demo.mp4).

## Install

Add the official marketplace and install the plugin:

```bash
codex plugin marketplace add Rodriguez-Diego-web/taskara-codex-plugin
codex plugin add taskara@taskara-official
```

Restart the Codex desktop app after installation or an update so the plugin files and tool inventory reload. When Taskara is used for the first time, complete the OAuth consent flow in your browser.

If Codex does not start the OAuth flow automatically, run:

```bash
codex mcp login taskara --scopes taskara:read,taskara:write
```

## What Codex can do

The direct Taskara MCP connection currently exposes:

- list organizations, customers, service objects, employees, catalog articles, tasks, schedule occurrences and invoices, with pagination
- read an owner/admin overview of staffing gaps, tasks and customer invoice balances, with explicit coverage and completeness
- read organization settings and update supported preferences when requested
- create tasks and unpublished schedule entries
- assign an explicitly confirmed replacement team to an unpublished one-off schedule draft, with concurrent-change checks
- create confirmed, catalog-based, unsent invoice drafts with exact quantities, agreed prices, VAT and retry protection

Taskara membership, organization roles, and OAuth scopes are enforced on every request. The bundled skill uses the Taskara web app only when a workflow is not yet available through MCP.

Invoice drafts reserve an invoice number but are never sent by the plugin. Actual-time billing, manual non-catalog invoice positions, quote creation, plan publication and recurring or published team changes use the Taskara web review flow. Invoice creation and team changes require an explicit review and confirmation; missing prices and ambiguous records are not guessed.

You may dictate requests through your client's speech input. Taskara does not record audio; availability of plugin tools during live voice depends on the client.

## Example prompts

- “Show today’s Taskara schedule and urgent tasks.”
- “List the open tasks for my organization.”
- “Create a high-priority Taskara task for tomorrow.”
- “Schedule this object for Friday at 09:00.”
- “Show this week's unassigned jobs and outstanding customer invoices.”
- “Prepare an unsent invoice draft from these catalog services and show me the prices before saving.”
- “Assign these employees to this unpublished one-off job after I confirm the team.”

## Privacy and security

- OAuth authorization happens on `taskara.de`.
- Codex never receives your Taskara password.
- Read and write access can be removed with `codex mcp logout taskara`.
- Taskara’s normal organization and role permissions remain authoritative.
- Privacy policy: [taskara.de/datenschutz](https://taskara.de/datenschutz)
- Terms: [taskara.de/agb](https://taskara.de/agb)

Please report security issues privately as described in [SECURITY.md](SECURITY.md).

## Repository layout

```text
.agents/plugins/marketplace.json
plugins/taskara/
  .codex-plugin/plugin.json
  .mcp.json
  assets/
  skills/
```

The Taskara name, logo, and brand assets are © Taskara. All rights reserved.
