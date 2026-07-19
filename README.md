# Taskara for Codex

The official public Codex plugin for [Taskara](https://taskara.de), the back-office platform for cleaning and facility-service teams.

Taskara connects to Codex through the production MCP endpoint at `https://taskara.de/api/mcp`. Authentication uses Taskara OAuth with PKCE. Your password stays on Taskara and is never shared with Codex.

## Install

Add the official marketplace and install the plugin:

```bash
codex plugin marketplace add Rodriguez-Diego-web/taskara-codex-plugin
codex plugin add taskara@taskara-official
```

Restart the ChatGPT desktop app or start a new Codex task after installation. When Taskara is used for the first time, complete the OAuth consent flow in your browser.

If Codex does not start the OAuth flow automatically, run:

```bash
codex mcp login taskara --scopes taskara:read,taskara:write
```

## What Codex can do

The direct Taskara MCP connection currently exposes:

- list organizations
- list customers
- list service objects
- list employees
- list tasks
- list schedule occurrences
- create tasks
- create schedule entries

Taskara membership, organization roles, and OAuth scopes are enforced on every request. The bundled skill uses the Taskara web app only when a workflow is not yet available through MCP.

## Example prompts

- “Show today’s Taskara schedule and urgent tasks.”
- “List the open tasks for my organization.”
- “Create a high-priority Taskara task for tomorrow.”
- “Schedule this object for Friday at 09:00.”

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
