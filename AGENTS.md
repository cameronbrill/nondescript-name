# AGENTS.md

This repository is for ai-company: an open-source AI operating system for building, launching, and operating a solo SaaS company with high scrutiny, high quality, auditability, and approval-by-policy.

## Current Phase

The repository is in the seed phase.

Do not write application code until the stack decision backlog has been resolved enough to support the scaffold.

Current priority:

- preserve the product vision
- enumerate decisions before making them
- avoid premature technical commitments
- keep the repository public-safe
- prepare the project for deliberate architecture work
- preserve blessed seed tooling decisions

## North Star

ai-company should make it possible for AI to build and operate meaningful parts of a company while the founder sleeps.

The product must not achieve autonomy by hiding risk. It must achieve autonomy through explicit policy, typed capabilities, approval-by-exception, quality gates, and complete auditability.

## Non-Negotiable Principles

1. Quality over speed when actions affect production, users, money, security, or trust.
2. Approval-by-policy, not approval-for-everything.
3. No invisible production actions.
4. Every meaningful agent action must have intent, context, risk, status, and audit trail.
5. Agents must act through explicit capabilities, not raw uncontrolled access.
6. Secrets, credentials, customer data, and private/internal datasets must never be committed.
7. ai-company is public by default, including production execution logic and commercial connectors.
8. Public code must still be safe: safety comes from permissions, policies, tests, reviews, and credential hygiene, not secrecy.
9. Major technical decisions require an ADR or a documented decision entry.
10. Do not invent stack choices casually. If a stack choice is unresolved, mark it `TBD` and preserve the decision for a dedicated deep dive.
11. Use Buildkite for repository CI, not GitHub Actions.
12. Use Plane for this repository's issue and project tracking, not GitHub Issues.
13. Use mise for task running, tool version pinning, and committed tool lockfiles.
14. Use Renovate for automated dependency maintenance.
15. Use fnox for secrets management and Infisical as the fnox remote provider when encrypted in-repo secrets are insufficient. Do not add `.env` or `.env.example` files.
16. Use Infisical for secret scanning.
17. Use pitchfork for process and daemon management when daemons exist.
18. Use hk for git hooks and project checks.
19. Use dprint for formatting orchestration. Add language-specific formatters only when the language decision is blessed.
20. Use cargo-binstall to accelerate cargo-installed seed CLIs; this does not bless Rust as the application language.
21. Use Aviator CLI for stacked PRs, Aviator MergeQueue for merge queue, and Aviator Releases for release management.
22. Use communique for release notes unless a later decision supersedes it.
23. Use React Router and TypeScript for the web app/control-plane UI when app code begins.
24. Use Go for company CLIs when CLI code begins.

## Dogfood Context

Night Shift is the first canonical customer and product dogfood case.

Night Shift is the AI first responder for production incidents. The MVP for ai-company is ready only when Night Shift has been built, launched, and operated through ai-company workflows that include real production launch/write capability under explicit trust policies.

ai-company is also a dogfood company, but it requires tighter founder oversight before MVP.

## Working Rules For Agents

- Read `README.md`, this file, and all docs before making structural changes.
- Do not scaffold application code during the seed phase unless explicitly instructed.
- Do not choose a blessed stack unless the task is specifically to make or record that decision.
- Do not turn repository tooling choices into product integration requirements. Product integrations must use typed capabilities and provider adapters unless a later ADR explicitly narrows that surface.
- Prefer small, reviewable documentation changes over broad rewrites.
- When changing doctrine, update related docs so the repo remains internally consistent.
- When a decision is made, record it in the decision system and create an ADR if it affects architecture.
- Treat `docs/08-stack-decision-backlog.md` as the source of truth for unresolved stack decisions.
- Treat `docs/adr/003-react-router-typescript-web-ui.md` as the source of truth for the blessed web UI and company CLI language decision.
- Never commit real secrets, credentials, tokens, customer data, private keys, production incident data, or private/internal datasets.
- Do not add GitHub Actions workflows or GitHub Issue templates.
- Do not add dotenv example files. Document fnox secret names or config instead.
- Run repository checks through `mise run check` when tooling is available.
- Run formatting through `mise run fmt` or `mise run fmt-check` when formatting is relevant.
- Run secret scanning through `mise run secret-scan` when secret exposure is relevant.
- Treat code review methodology and tooling as unresolved until `docs/10-code-review-methodology.md` is replaced by a blessed decision.

## Definition Of Done

A task is not done unless:

- the repository remains internally consistent
- relevant docs are updated
- unresolved decisions are marked clearly
- public/private boundaries are preserved
- no secrets are committed
- any commands required for verification have been run, or the reason they were not run is stated
