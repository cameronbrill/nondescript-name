# Contributing

ai-company is early and doctrine-first.

Before contributing code, read:

- `README.md`
- `AGENTS.md`
- `docs/00-product-constitution.md`
- `docs/07-decision-system.md`
- `docs/08-stack-decision-backlog.md`
- `docs/adr/001-seed-tooling-baseline.md`

## Current Contribution Priority

The current priority is not app implementation.

The current priority is to make the product doctrine, decision process, dogfood strategy, and future stack decisions clear enough that implementation can happen deliberately.

## Contribution Rules

- Do not introduce application code unless the Plane work item explicitly asks for it.
- Do not bless a stack choice without updating the decision system.
- Do not add secrets, credentials, customer data, or private datasets.
- Do not add `.env` or `.env.example` files.
- Do not add GitHub Actions workflows or GitHub Issue templates.
- Prefer small, reviewable changes.
- Preserve the goal of 100% open-source core logic, including execution logic and connectors.
- Update related docs when changing product or architecture doctrine.

## Work Tracking

Plane is the blessed issue and project tracker.

GitHub Issues are rejected for now and disabled in repository settings. Public contribution intake is a future decision.

## Pull Requests

Aviator CLI is the blessed stacked PR workflow. Aviator MergeQueue is the blessed merge queue.

Use Aviator for stacked PRs once contribution workflows begin. Queue merge-ready work through Aviator MergeQueue rather than manually merging through GitHub.

## Tooling

Use mise as the task entrypoint and tool-version source.

Useful commands:

- `mise install`
- `mise run check`
- `mise run ci`
- `mise run fmt`
- `mise run fmt-check`
- `mise run secret-scan`

Use fnox for secrets, Infisical for remote secrets when encrypted in-repo secrets are insufficient and for secret scanning, hk for hooks/checks, Buildkite for CI, dprint for formatting orchestration, cargo-binstall for cargo-installed seed CLI acceleration, Renovate for dependency maintenance, pitchfork for future daemon management, Aviator for stacked PRs/merge queue/releases, and communique for release notes.

## Decision Changes

If a change affects architecture, stack, trust boundaries, execution policy, data model, or public/private posture, add or update an ADR.

Use `docs/adr/000-template.md`.
