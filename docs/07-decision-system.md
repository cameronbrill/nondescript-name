# Decision System

ai-company should make decisions deliberately.

The decision system exists to prevent accidental architecture, accidental stack choices, and accidental doctrine changes.

## Decision Statuses

TBD: the decision has not been made and needs a dedicated discussion.

Proposed: a specific answer exists, but it is not yet approved.

Blessed: the decision is approved and should be followed.

Allowed later: the decision is not part of the current phase, but the project should not block future adoption.

Rejected for now: the option should not be used in the current phase, but may be revisited.

Superseded: the decision was replaced by a later decision.

## Decision Types

Doctrine decision: changes product principles, MVP definition, dogfood rules, open-source posture, or quality philosophy.

Stack decision: chooses tools, languages, services, vendor adapters, frameworks, task runners, hosting, testing, formatting, linting, observability, auth, database, search, model providers, or environment management.

Architecture decision: changes component boundaries, data flow, trust boundaries, execution model, integration model, or persistence model.

Policy decision: changes what agents may do, when approval is required, or how risk is evaluated.

Implementation decision: affects code structure but does not change product doctrine or architecture.

## When An ADR Is Required

Create or update an ADR when a decision:

- blesses a stack choice
- changes architecture boundaries
- affects production execution
- affects trust, autonomy, approval, or auditability
- affects public/private boundaries
- changes data ownership or persistence
- would be expensive to reverse later

Use `docs/adr/000-template.md`.

## Decision Entry Format

Each important decision should include:

- title
- status
- date
- owner
- context
- decision
- rationale
- options considered
- consequences
- revisit trigger

## Stack Decision Backlog

`docs/08-stack-decision-backlog.md` is the source of truth for unresolved stack decisions.

Do not scaffold application code until enough stack decisions are marked `blessed` to support the scaffold.

## Blessed Seed Tooling

`docs/adr/001-seed-tooling-baseline.md` blesses a small amount of seed-phase tooling before the full app stack is decided.

These seed tooling choices govern repository operations only. They do not create hard product dependencies or bypass typed capability and provider-adapter boundaries.

Blessed for repository operations:

- Buildkite for CI.
- Plane for this repository's issue and project tracking.
- mise for task running, tool version pinning, and committed tool lockfiles.
- Renovate for automated dependency maintenance.
- fnox for secrets management.
- Infisical as the fnox remote provider when encrypted in-repo secrets are insufficient.
- Infisical for secret scanning.
- pitchfork for process and daemon management.
- hk for git hooks and project checks.
- dprint for formatting orchestration.
- cargo-binstall for cargo-installed seed CLI acceleration.
- Aviator CLI for stacked PRs.
- Aviator MergeQueue for merge queue.
- Aviator Releases for release management.
- communique for release notes.

Rejected for now:

- GitHub Actions.
- GitHub Issues.
- committed `.env` files.
- committed `.env.example` files.

## How To Make A Decision

1. Name the decision clearly.
2. Define what will break if the decision is wrong.
3. List realistic options.
4. State a recommendation.
5. Record tradeoffs.
6. Mark the status.
7. Update related docs.
8. Create an ADR when required.

## Seed-Phase Rule

When uncertain, write `TBD` rather than inventing a default.

The goal of the seed phase is not to decide everything. The goal is to make every important undecided item visible.
