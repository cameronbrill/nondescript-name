# ai-company

ai-company is an open-source attempt to build an AI operating system that can help a solo SaaS founder build, launch, and operate a company with high scrutiny, high quality, auditability, and approval-by-policy.

The north star is ambitious: AI should be able to build and operate meaningful parts of a company while the founder sleeps. The constraint is equally important: agents must act inside explicit policies, quality gates, trust boundaries, and audit trails.

## Current Status

This repository is in its seed phase.

The current goal is not to ship app code. The current goal is to define the operating doctrine, decision system, dogfood strategy, quality bar, open-source posture, and stack decision backlog before implementation begins.

## Product Thesis

Solo SaaS founders should be able to get production-grade leverage without hiring a full team first.

ai-company should become a governed agent team and operating system that can:

- understand a company's context
- plan business-building work
- produce and review artifacts
- stage product and engineering changes
- execute approved production actions
- log every meaningful action
- escalate uncertain or risky work to the founder

## Initial Users

The initial intended user profile is a technical solo SaaS founder.

Before MVP, the only real user is the founder of this repo. External users are out of scope until Night Shift has been dogfooded through real production launch/write workflows under the project's constraints.

## Dogfood Companies

Two dogfood companies shape the product:

- Night Shift, the first canonical customer product
- ai-company itself, with tighter founder oversight before MVP

Night Shift is the primary MVP proof case. ai-company should also use its own workflow over time, but with additional caution while the system is immature.

## MVP Definition

The MVP is ready when Night Shift has been built, launched, and operated through ai-company workflows that include real production launch/write capability under explicit trust policies.

The MVP is not just a planning tool. It must eventually prove governed execution.

## What Is Intentionally Undecided

The technical stack is not blessed yet.

Some seed-phase tooling is blessed in `docs/adr/001-seed-tooling-baseline.md`: Buildkite, Plane, Aviator, mise, fnox, Infisical, Renovate, pitchfork, hk, dprint, cargo-binstall, and communique.

Before application code is written, the project must deliberately decide the remaining stack across repo organization, languages, environment management, app framework, database, auth, workflow orchestration, observability, hosting, search, testing, formatting, linting, typechecking, model providers, integrations, and release process.

See `docs/08-stack-decision-backlog.md`.

## Repository Map

- `AGENTS.md` defines standing instructions for AI coding agents.
- `docs/00-product-constitution.md` defines the enduring product constraints.
- `docs/01-vision-and-operating-doctrine.md` defines the operating philosophy.
- `docs/02-dogfood-strategy.md` defines how Night Shift and ai-company shape the MVP.
- `docs/03-mvp-definition.md` defines what must be true before the MVP ships.
- `docs/04-trust-and-autonomy-principles.md` defines approval-by-policy.
- `docs/05-quality-principles.md` defines the quality bar.
- `docs/06-open-source-strategy.md` defines the public-by-default posture.
- `docs/07-decision-system.md` defines how choices become blessed.
- `docs/08-stack-decision-backlog.md` enumerates stack decisions still required.
- `docs/09-build-sequence.md` defines the high-level sequence from seed to app code.
- `docs/10-code-review-methodology.md` records the code review methodology placeholder.
- `docs/adr/000-template.md` is the template for architecture decision records.
- `docs/adr/001-seed-tooling-baseline.md` blesses seed-phase project tooling.
- `docs/adr/002-vendor-integration-abstraction.md` requires product integrations to use swappable provider adapters.
- `.aviator/config.yml` defines the Aviator MergeQueue trigger label.
- `dprint.json` defines formatting orchestration for docs/config files while deferring language-specific formatters.
- `mise.toml` pins seed tooling, enables `mise.lock`, sets a three-day minimum release age, disables task auto-install, and defines task entrypoints.
- `mise.lock` locks seed tool versions and available tool artifacts.
- `hk.pkl` defines project checks and git-hook orchestration.
- `renovate.json` configures automated dependency maintenance.
- `.buildkite/pipeline.yml` defines the CI entrypoint.
- `communique.toml` defines release-note context and style.

## Development Rule

Do not scaffold application code until the stack decision backlog has been reviewed and enough decisions are marked `blessed` to support the scaffold.

## Open Source

ai-company is intended to be 100% open source, including production execution logic and commercial connectors.

Secrets, credentials, customer data, and private/internal datasets must never be committed.

This repo intentionally does not include `.env` or `.env.example` files. Secrets are managed through fnox, with Infisical as the remote provider when encrypted in-repo secrets are not sufficient.

GitHub Actions and GitHub Issues are rejected for now. CI runs through Buildkite, project work is tracked in Plane, and GitHub Issues are disabled in the repository settings.

Aviator is used for stacked PRs, merge queue, and release management. Renovate is used for automated dependency maintenance. Infisical is used for secret scanning. dprint is used for formatting orchestration; language-specific formatters are added only when corresponding language decisions are blessed.

Repository tooling choices are not intended to force product users into the same vendors. Product integrations should recommend strong defaults while allowing existing accounts and alternative providers through typed capabilities and provider adapters.
