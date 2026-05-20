# Build Sequence

This document defines the high-level sequence from seed repo to MVP.

It is intentionally not a detailed implementation plan. Detailed implementation plans should come after the relevant stack and architecture decisions are blessed.

## Phase 0: Seed The Repository

Goal: create the product doctrine and decision framework.

Deliverables:

- repository identity files
- agent instructions
- product constitution
- vision and operating doctrine
- dogfood strategy
- MVP definition
- trust and autonomy principles
- quality principles
- open-source strategy
- decision system
- stack decision backlog
- ADR template
- seed tooling baseline
- Buildkite CI entrypoint
- Aviator MergeQueue config
- mise task and tool-version entrypoint
- mise tool lockfile
- hk project checks
- dprint formatting orchestration config
- Renovate dependency maintenance config
- Infisical secret scanning entrypoint
- cargo-binstall acceleration for cargo-installed seed CLIs
- communique release-note config

Application code is out of scope.

GitHub Actions and GitHub Issues are out of scope and rejected for now. Work is tracked in Plane, CI runs through Buildkite, stacked PRs and merge queue run through Aviator, automated dependency maintenance runs through Renovate, secret scanning runs through Infisical, and formatting orchestration runs through dprint.

## Phase 1: Stack Deep Dive

Goal: make deliberate stack decisions before app scaffolding.

Deliverables:

- reviewed stack decision backlog
- blessed required-before-scaffold decisions
- rejected-for-now options
- allowed-later options
- ADRs for major choices
- updated build sequence if needed
- code review methodology and tooling decision

Already-blessed seed tooling should be treated as existing constraints unless explicitly revisited through the decision system.

Application code is still out of scope unless the founder explicitly chooses to scaffold.

## Phase 2: Architecture Deep Dive

Goal: define enough architecture to build the first scaffold without painting the project into a corner.

Deliverables:

- system architecture spec
- domain model draft
- trust and policy architecture draft
- agent execution architecture draft
- integration capability model draft
- data and audit model draft
- MVP slice implementation plan

The architecture should preserve the requirement for real production launch/write capability under explicit policy.

## Phase 3: App Scaffold

Goal: create the minimal application foundation using blessed stack decisions.

Deliverables should be defined after Phase 1 and Phase 2.

Expected categories:

- app shell
- local development setup
- CI checks
- test setup
- type/lint/format tooling
- database setup if blessed
- auth setup if blessed
- initial deploy path if blessed

The scaffold should not include speculative product features.

## Phase 4: Core Domain And Audit Trail

Goal: implement the core concepts needed for governed work.

Expected concepts:

- company context
- work requests
- work packets
- agent actions
- approvals
- artifacts
- quality gates
- audit records

The exact data model must be decided before implementation.

## Phase 5: Night Shift Dogfood Loop

Goal: use ai-company to advance Night Shift.

Expected flow:

1. Capture Night Shift context.
2. Submit Night Shift work requests.
3. Create governed work packets.
4. Produce artifacts and plans.
5. Stage changes.
6. Run quality gates.
7. Request approvals when policy requires.
8. Execute approved production launch/write actions.
9. Record audit evidence.
10. Review outcomes and update context.

## Phase 6: MVP Readiness Review

Goal: decide whether the product is ready for users beyond the founder.

MVP readiness requires evidence from `docs/03-mvp-definition.md`.

Do not ship external users merely because the app exists. Ship only when the Night Shift dogfood proof is credible.
