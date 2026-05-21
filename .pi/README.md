# Project-local Pi configuration

This directory contains a small amount of project-local Pi configuration for ai-company repository
workflows. It is developer tooling only; it is not application code, product runtime, product
connector code, or a stack decision.

## What is configured

- `.pi/settings.json` pins project-local Pi packages:
  - `pi-subagents` for parent-orchestrated helper agents.
  - `pi-mcp-adapter` for MCP access through Pi.
- `.mcp.json` configures the Plane MCP server using lazy OAuth-based access.
- `.pi/skills/ai-company-plane/SKILL.md` gives the agent a compact workflow for using Plane safely.
- `.pi/agents/*.md` defines a small set of read-only ai-company advisory agents.

## Plane MCP usage

After pulling these files:

1. Restart Pi or run `/reload` from the repo root.
2. Open `/mcp` to inspect MCP status.
3. Authenticate Plane with `/mcp-auth plane` if prompted.
4. Use `/skill:ai-company-plane` when asking the agent to work with Plane.

The MCP adapter keeps Plane tools behind the compact `mcp` proxy by default. This avoids loading many
Plane tool schemas into every prompt.

Example MCP flow for the agent:

```text
mcp({ connect: "plane" })
mcp({ server: "plane" })
mcp({ search: "issue project" })
mcp({ describe: "<tool-name>" })
mcp({ tool: "<tool-name>", args: "{...json...}" })
```

Do not commit Plane OAuth tokens, API keys, cookies, exports containing private data, or work item
content that includes secrets/customer data.

## Boundaries

- Plane is the issue/project tracker for this repository; do not add GitHub Issue templates.
- Keep product integrations abstract through typed capabilities/provider adapters unless a later ADR
  narrows the surface.
- Do not scaffold app code from Pi resources.
- Do not add `.env` or `.env.example` files.
- Do not add Night Shift-specific local resources to this repository.
