---
name: ai-company-plane
description: Guides safe use of Plane through Pi's MCP adapter for this repository. Use when creating, finding, triaging, or updating Plane work items, projects, cycles, or labels for ai-company.
---

# ai-company Plane workflow

## When to use

Use this skill when the user asks to work with Plane, repository tasks, project tracking, issue
triage, work packets, or backlog updates for ai-company.

## Source-of-truth files

- `.pi/settings.json` — pins `pi-mcp-adapter` for Pi.
- `.mcp.json` — configures the project-local Plane MCP server.
- `CONTRIBUTING.md` — states that this repository uses Plane, not GitHub Issues.
- `AGENTS.md` — repository non-negotiables and seed-phase rules.
- `docs/07-decision-system.md` — decision hygiene.
- `docs/08-stack-decision-backlog.md` — stack backlog source of truth.

## Setup checks

1. If Plane tools are not available, ask the user to run `/reload` or restart Pi.
2. Use `/mcp` to inspect MCP server status when interactive.
3. Use `/mcp-auth plane` if Plane requires authentication.
4. Do not ask for or print Plane tokens, cookies, API keys, or OAuth credentials.

## MCP usage pattern

Use the compact MCP proxy rather than assuming direct Plane tools are available:

```text
mcp({ connect: "plane" })
mcp({ server: "plane" })
mcp({ search: "issue project cycle label" })
mcp({ describe: "<tool-name>" })
mcp({ tool: "<tool-name>", args: "{...json...}" })
```

`args` must be a JSON string, not an object.

## Workflow

1. Clarify whether the user wants read-only lookup, draft planning, or a Plane mutation.
2. For read-only work, search/list Plane items and summarize with Plane IDs/links where available.
3. For mutations, restate the intended change before calling the Plane tool when the action could
   affect project tracking, priorities, ownership, status, or public contributor workflow.
4. Keep work item text public-safe: no secrets, credentials, customer data, private incident data,
   private datasets, or sensitive logs.
5. Link Plane work to repository docs or ADR/backlog entries when relevant.
6. Preserve unresolved decisions as `TBD`; do not mark stack or architecture choices blessed from a
   Plane update alone.

## Output format

- Plane action requested
- MCP/server status if checked
- Items found or changed, with IDs/links when available
- Public-safety or decision-system concerns
- Follow-up repository docs/ADR/backlog updates needed

## Non-goals

- Do not use GitHub Issues for this repository.
- Do not create app scaffold or product runtime code.
- Do not turn Plane MCP access into a product integration requirement.
