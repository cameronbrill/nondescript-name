# Stack Decision Backlog

This document is the source of truth for unresolved stack decisions.

Do not scaffold application code until this backlog has been reviewed and enough decisions are marked `blessed` to support the scaffold.

The goal is to enumerate decisions before making them.

## Status Legend

TBD: no decision has been made.

Proposed: a candidate decision exists but is not approved.

Blessed: the decision is approved and should be followed.

Allowed later: not part of the current phase, but compatible with future direction.

Rejected for now: should not be used in the current phase.

Superseded: replaced by a later decision.

## Decision Depth Legend

Quick: low-risk decision that can be made with limited research.

Normal: meaningful tradeoffs; compare options before deciding.

Deep dive required: expensive to reverse, product-defining, or affects many other choices.

## Seed-Phase Rule

Every item below is `TBD` unless explicitly marked otherwise.

No agent should infer a stack choice from examples, prior preferences, or common defaults.

## Blessed Seed Tooling

The following seed-phase decisions are blessed by `docs/adr/001-seed-tooling-baseline.md`:

- CI: Buildkite.
- Issue and project tracking: Plane.
- Task running: mise.
- Tool version pinning: mise.
- Tool lockfile: mise.lock.
- Tool minimum release age: three days.
- Dependency maintenance: Renovate.
- Secrets management: fnox.
- fnox remote secrets provider: Infisical when encrypted in-repo secrets are insufficient.
- Secret scanning: Infisical.
- Process and daemon management: pitchfork.
- Git hooks and project checks: hk.
- Formatting orchestration: dprint.
- Cargo-installed seed CLI acceleration: cargo-binstall.
- Stacked PRs: Aviator CLI.
- Merge queue: Aviator MergeQueue.
- Release management: Aviator Releases.
- Release notes: communique.

The following are rejected for now:

- GitHub Actions.
- GitHub Issues.
- committed `.env` files.
- committed `.env.example` files.

## Repository And Project Organization

### Repository Shape

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold

Questions to resolve: single app repo, monorepo, package boundaries, docs/specs layout, examples layout, connector layout.

### Workspace And Package Management

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: app scaffold

Questions to resolve: package manager, workspace manager, lockfile policy, dependency update policy.

### Issue And Project Tracking

Status: Blessed for this repository; product integration abstraction blessed separately

Decision owner: founder

Decision depth: normal

Decision required before: seed collaboration

Decision: Use Plane for this repository's issue and project tracking. Do not use GitHub Issues for this repository.

Repository setting: GitHub Issues are disabled.

Product note: ai-company should recommend Plane for issue tracking, but product integrations must allow other providers such as Linear, Jira, GitHub Issues, or existing user accounts through provider adapters.

### Stacked PR Workflow

Status: Blessed

Decision owner: founder

Decision depth: normal

Decision required before: first pull request workflow

Decision: Use Aviator CLI for stacked PRs.

Questions still to resolve: branch naming, stack size expectations, when stacked PRs are required, local `av init` workflow, and how stack review maps to code review policy.

### Merge Queue

Status: Blessed

Decision owner: founder

Decision depth: normal

Decision required before: protected main branch

Decision: Use Aviator MergeQueue for merge queue.

Current repository config: `.aviator/config.yml` uses the `mergequeue` trigger label.

External setup required: install/configure Aviator on the GitHub repository and exclude Aviator temporary `mq-tmp-*` branches from Buildkite branch triggers with `!mq-tmp-*`.

### Task Runner And Build Orchestration

Status: Blessed for task running; app build orchestration TBD

Decision owner: founder

Decision depth: normal

Decision required before: app scaffold

Decision: Use mise for repository task entrypoints, tool version pinning, and committed tool lockfiles.

Current repository config: `mise.toml` enables `mise.lock`, sets `minimum_release_age = "3d"` for tool resolution, and disables mise task auto-install. Run `mise install` before repository tasks. Buildkite ignores agent-global mise config.

Questions still to resolve: affected-package tasks, cache behavior, app build orchestration, CI parity after the app stack is chosen.

### Versioning And Release Structure

Status: Blessed for release management and release-note tooling; versioning TBD

Decision owner: founder

Decision depth: normal

Decision required before: first release

Decision: Use Aviator Releases for release management and communique for release notes unless a later decision supersedes communique.

Questions still to resolve: app versioning, package versioning, changelog format, release tags, connector releases, Aviator Release Projects, Buildkite release/deploy pipeline integration.

## Languages And Runtimes

### Primary Application Language

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold

Questions to resolve: primary language for web app, domain logic, integrations, workflows, and tests.

Note: `rust@1.88.0` and `cargo-binstall@1.19.1` are pinned in `mise.toml` only to support and accelerate cargo-installed seed CLIs. They do not decide the application language.

### Secondary Language Policy

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: specialized tooling

Questions to resolve: whether to allow separate languages for evals, data tooling, model experimentation, CLIs, or infrastructure.

### Runtime Versions

Status: Blessed for version pinning mechanism; runtime versions TBD

Decision owner: founder

Decision depth: normal

Decision required before: app scaffold

Decision: Use mise for tool version pinning and committed `mise.lock` files.

Current repository policy: resolve mise tools only after a three-day minimum release age unless an explicit pin is intentionally changed.

Questions still to resolve: runtime versions, upgrade cadence, local/CI/prod parity.

### Module And Build Format

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: shared packages

Questions to resolve: module format, package exports, server/client boundaries, generated type artifacts.

## Web Application

### Frontend Framework

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold

Questions to resolve: app framework, routing model, rendering model, server/client split, deployment compatibility.

### UI Component Strategy

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: product UI implementation

Questions to resolve: component library, headless components, custom design system, accessibility baseline.

### Styling And Design System

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: product UI implementation

Questions to resolve: styling framework, tokens, themes, typography, dark mode, design documentation.

### Client State And Data Fetching

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: interactive app features

Questions to resolve: local state, server state, caching, optimistic updates, mutations, realtime subscriptions.

### Forms And Validation

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: data-entry flows

Questions to resolve: form library, validation schema strategy, shared server/client validation.

### Realtime Interface

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: live agent run UI

Questions to resolve: server-sent events, WebSockets, polling, hosted realtime, event persistence.

## Backend And API

### Backend Framework

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold

Questions to resolve: integrated full-stack backend, separate API service, serverless functions, long-running services.

### API Style

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: API implementation

Questions to resolve: REST, RPC, GraphQL, OpenAPI, typed client generation, public API boundaries.

### Domain Layer Boundaries

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: core domain models

Questions to resolve: where business rules live, how domain transitions are tested, how provider-specific logic is isolated.

### Authentication

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: user accounts

Questions to resolve: auth provider, session model, OAuth strategy, service accounts, local dev auth.

### Authorization And Permissions

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: multi-actor workflows

Questions to resolve: user roles, agent permissions, policy evaluation, capability permissions, organization boundaries.

### Tenancy Model

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: external users

Questions to resolve: single-user pre-MVP, future organizations, data isolation, tenant IDs, permission boundaries.

## Data And Persistence

### Primary Database

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold

Questions to resolve: database engine, managed provider, local dev parity, backup/restore, audit storage.

### Data Access Layer

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: core domain models

Questions to resolve: ORM, query builder, raw SQL policy, migrations, generated types.

### Migration Strategy

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: first persistent schema

Questions to resolve: migration tool, migration tests, rollback policy, production migration approval.

### ID And Timestamp Strategy

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: domain schemas

Questions to resolve: ID format, stable public IDs, internal IDs, timestamp format, clock source.

### Audit Log Persistence

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: agent execution

Questions to resolve: append-only storage, immutability guarantees, redaction, retention, query patterns, evidence attachments.

### File And Artifact Storage

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: artifact registry

Questions to resolve: blob storage, local dev storage, generated artifact versioning, public/private artifact policy.

### Cache

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: performance work

Questions to resolve: whether cache is needed, cache provider, invalidation, local dev parity.

### Search

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: company context retrieval

Questions to resolve: full-text search, semantic search, hybrid search, indexing, result explainability.

### Vector Storage And Retrieval

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: semantic company memory

Questions to resolve: vector DB, database extension, embedding provider, retrieval policy, deletion, evals.

## Agent System And Execution

### Agent Orchestration Model

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: agent implementation

Questions to resolve: deterministic templates, model calls, role-based agents, workflow graph, state machine, human gates.

### Durable Workflow Runner

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: overnight execution

Questions to resolve: managed workflow service, self-hosted runner, queue-backed jobs, retries, timeouts, resumability.

### Queue And Background Jobs

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: async execution

Questions to resolve: queue provider, worker runtime, concurrency, idempotency, failure handling, local dev.

### Scheduling

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: overnight work cycles

Questions to resolve: cron, user schedules, timezone handling, missed runs, maintenance windows.

### Process And Daemon Management

Status: Blessed

Decision owner: founder

Decision depth: normal

Decision required before: local daemons or managed dev processes

Decision: Use pitchfork for process and daemon management when daemons exist.

Current note: No `pitchfork.toml` is needed during the seed phase because there are no daemons yet.

### Capability System

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: production writes

Questions to resolve: typed capability contracts, capability registry, permission binding, risk metadata, provider adapter boundaries, test strategy.

### External Vendor Integration Abstraction

Status: Blessed

Decision owner: founder

Decision depth: deep dive required

Decision required before: connector implementation

Decision: Product integrations must use typed capabilities and provider adapters. Blessed-path vendors are recommended defaults, not hard dependencies, unless a later ADR explicitly narrows a product surface.

Examples: recommend Plane for issue tracking while supporting Linear, Jira, GitHub Issues, and existing user accounts. Recommend Codeberg or Forgejo for code forge/source control where appropriate while supporting GitHub and GitLab.

Related ADR: `docs/adr/002-vendor-integration-abstraction.md`.

### Policy Engine

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: approval-by-policy

Questions to resolve: policy language, policy storage, evaluation runtime, explainability, override handling.

### Approval System

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: production writes

Questions to resolve: approval records, approval scopes, expiration, delegation, replay safety, audit linkage.

### Sandbox And Safe Execution

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: untrusted agent actions

Questions to resolve: code execution sandbox, integration mocks, preview environments, network restrictions, secrets exposure.

### Model Provider Strategy

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: live AI features

Questions to resolve: provider abstraction, provider choice, model routing, cost controls, fallback behavior, prompt/version management.

### Evals And Agent Quality

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: autonomous execution claims

Questions to resolve: eval harness, test datasets, private vs public evals, regression checks, artifact scoring, launch gates.

## Integrations And Connectors

### Source Control Connector

Status: TBD; vendor abstraction blessed

Decision owner: founder

Decision depth: deep dive required

Decision required before: code-change workflows

Questions to resolve: provider capability contract, Codeberg/Forgejo recommendation, GitHub and GitLab support, app installation, repo permissions, branch strategy, pull request automation, merge policy.

### Issue Tracker Connector

Status: TBD; vendor abstraction blessed

Decision owner: founder

Decision depth: normal

Decision required before: work tracking product integration

Questions to resolve: issue-tracking capability contract, Plane recommendation, Linear/Jira/GitHub Issues support, existing account onboarding, project mapping, labels/status mapping, comments, attachments, audit linkage.

### Hosting And Deployment Connector

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: production launch/write MVP proof

Questions to resolve: deployment provider, previews, production deploy approval, rollback, environment variables, logs.

### Observability Connector

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: Night Shift incident workflows

Questions to resolve: logs, metrics, traces, alert providers, incident context, read/write permissions.

### Incident Management Connector

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: Night Shift dogfood

Questions to resolve: incident providers, escalation policies, remediation permissions, simulations, audit requirements.

### Communication Connector

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: notification workflows

Questions to resolve: Slack, email, internal summaries, customer-facing messages, approval before external sends.

### Billing Connector

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: paid product

Questions to resolve: billing provider, subscription actions, refunds, invoices, approval rules, high-risk restrictions.

### Customer Data Connector

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: customer operations

Questions to resolve: CRM/support providers, data minimization, permissions, redaction, audit requirements.

## Infrastructure And Environments

### Cloud Hosting

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold

Questions to resolve: hosting provider, serverless vs long-running, region, cost, scaling, lock-in, deployment model.

### Environment Management

Status: Rejected for dotenv files; broader environment strategy TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold

Decision: Do not commit `.env` or `.env.example` files.

Questions still to resolve: local/staging/prod environments, environment variables, config validation, preview environments.

### Secrets Management

Status: Blessed

Decision owner: founder

Decision depth: deep dive required

Decision required before: live integrations

Decision: Use fnox for secrets management. Use Infisical as the fnox remote provider when encrypted in-repo secrets are not sufficient.

Questions still to resolve: exact Infisical project/environment/path layout, encrypted-in-git vs remote-provider usage boundaries, rotation, local dev secrets, CI secrets, agent access boundaries.

### Continuous Integration

Status: Blessed

Decision owner: founder

Decision depth: normal

Decision required before: seed checks

Decision: Use Buildkite for CI.

Rejected for now: GitHub Actions.

Questions still to resolve: Buildkite agent environment, secrets access through fnox and Infisical, cache strategy, required pipeline checks.

### Infrastructure As Code

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: repeatable infrastructure

Questions to resolve: IaC tool, ownership, drift detection, production approval gates.

### Local Development

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: contributor onboarding

Questions to resolve: dev containers, local services, seed data, mock providers, one-command setup.

### Preview Environments

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: staged execution

Questions to resolve: preview deploys, seeded data, integration mocks, policy for preview actions.

## Observability And Operations

### Logging

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: production execution

Questions to resolve: structured logs, redaction, retention, correlation IDs, audit linkage.

### Metrics

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: production operations

Questions to resolve: app metrics, agent metrics, quality metrics, business metrics, alerting.

### Tracing

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: multi-step workflows

Questions to resolve: trace provider, workflow traces, tool-call traces, privacy.

### Error Tracking

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: production launch

Questions to resolve: provider, source maps, PII scrubbing, alert policies.

### Product Analytics

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: external users

Questions to resolve: analytics provider, privacy posture, self-hosting, event taxonomy.

## Quality Tooling

### Typechecking

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: app scaffold

Questions to resolve: typechecker, strictness, generated types, CI enforcement.

### Linting

Status: Blessed for hook/check orchestration; language-specific linters TBD

Decision owner: founder

Decision depth: normal

Decision required before: app scaffold

Decision: Use hk for git hooks and project check orchestration.

Questions still to resolve: language-specific linters, rules, import boundaries, security rules, CI enforcement.

### Formatting

Status: Blessed for orchestration; language-specific formatters TBD

Decision owner: founder

Decision depth: quick

Decision required before: app scaffold

Decision: Use dprint for formatting orchestration.

Current repository config: `dprint.json` includes docs/config formatters and intentionally defers language-specific formatters.

Questions still to resolve: markdown formatting, JSON/YAML formatting, language-specific formatters, formatter plugins, CI enforcement.

Allowed later: add individual formatters such as ruff, ssort, and oxfmt only when their corresponding language decisions are blessed.

### Unit Testing

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: domain models

Questions to resolve: test runner, assertion style, mocks, coverage expectations.

### Integration Testing

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: connectors

Questions to resolve: mocked integrations, contract tests, sandbox providers, live test policy.

### End-To-End Testing

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: MVP release

Questions to resolve: browser testing, auth setup, seeded data, CI runtime.

### Schema Validation

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: machine-readable specs

Questions to resolve: schema language, runtime validation, generated types, backwards compatibility.

### Security Scanning

Status: Blessed for secret scanning; broader security scanning TBD

Decision owner: founder

Decision depth: normal

Decision required before: app scaffold

Decision: Use Infisical for secret scanning.

Current repository config: `mise run secret-scan` runs `infisical scan --no-git --redact --no-color`.

Questions still to resolve: dependency vulnerability scanning, static analysis, fnox-aware secret checks, Infisical hosted repository scanning setup, CI failure policy after application code begins.

### Code Review Methodology And Tooling

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: app scaffold or first production-write workflow

Questions to resolve: PR review policy, stacked PR review flow with Aviator CLI, merge queue requirements with Aviator MergeQueue, human review expectations before MVP, AI-assisted review tooling, security review gates, architecture review gates, review checklist format, required checks before merge, review standards for production-write paths, connector review standards.

Current placeholder: `docs/10-code-review-methodology.md`.

### Dependency Management

Status: Blessed for Renovate; application dependency policy TBD

Decision owner: founder

Decision depth: normal

Decision required before: seed dependency updates

Decision: Use Renovate for automated dependency maintenance.

Current repository config: `renovate.json` uses `config:recommended`, disables the dependency dashboard because GitHub Issues are disabled, and sets a three-day minimum release age with strict internal checks.

Questions still to resolve: application dependency version ranges, language-specific lockfile policy, vulnerability triage, Renovate scheduling, automerge policy, and whether Renovate must run through a hosted app or a Buildkite/self-hosted job.

## Product And Business Systems

### Billing

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: external paid users

Questions to resolve: provider, pricing model, metering, billing permissions, refund restrictions.

### Email

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: user notifications

Questions to resolve: provider, transactional templates, marketing separation, approval for customer-facing sends.

### Feature Flags

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: external users

Questions to resolve: flag provider, local dev behavior, auditability, rollout policy.

### Documentation Tooling

Status: TBD

Decision owner: founder

Decision depth: quick

Decision required before: public docs site

Questions to resolve: docs site generator, API docs, ADR index, changelog.

### Release Notes

Status: Blessed

Decision owner: founder

Decision depth: normal

Decision required before: first release

Decision: Use communique for release notes.

Questions still to resolve: changelog policy, GitHub Release publishing policy, release PR flow, required tokens through fnox and Infisical.

### Release Management

Status: Blessed

Decision owner: founder

Decision depth: normal

Decision required before: first release

Decision: Use Aviator Releases for release management.

Questions still to resolve: release projects, environments, Buildkite build/deploy workflow integration, release approvals, rollback workflow, cherrypick workflow, required fnox and Infisical secrets.

## Compliance, Privacy, And Governance

### Privacy Model

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: customer data

Questions to resolve: data minimization, retention, deletion, subprocessors, logs, model-provider data use.

### Data Retention

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: audit implementation

Questions to resolve: audit retention, artifact retention, customer deletion requests, legal holds.

### Compliance Posture

Status: TBD

Decision owner: founder

Decision depth: deep dive required

Decision required before: enterprise users

Questions to resolve: SOC 2 path, security documentation, internal controls, evidence collection.

## Documentation And Specs

### Machine-Readable Specs

Status: TBD

Decision owner: founder

Decision depth: normal

Decision required before: code generation or API implementation

Questions to resolve: JSON Schema, OpenAPI, generated docs, schema versioning, examples.

### ADR Indexing

Status: TBD

Decision owner: founder

Decision depth: quick

Decision required before: many ADRs

Questions to resolve: naming, numbering, index file, status tracking.

## First Stack Deep-Dive Output

The dedicated stack conversation should produce:

- a recommended default for each required-before-scaffold decision
- explicit rejected-for-now alternatives
- allowed-later paths
- ADRs for major choices
- a revised app scaffold build plan
