# MVP Definition

## MVP Statement

The MVP is the first version of ai-company that can help build, launch, and operate Night Shift through governed workflows that include real production launch/write capability under explicit trust policies.

The MVP is not ready when the app can generate plans. The MVP is ready when the system has proven a safe execution loop on Night Shift.

## Pre-MVP User Scope

Before MVP, the only real user is the founder.

External users are not part of the pre-MVP scope. This lets the product optimize for dogfood truth instead of premature onboarding, pricing, multi-user support, or broad market polish.

## MVP Must Prove

The MVP must prove:

- company context can guide agent work
- founder requests can become governed work packets
- agents can produce useful, specific, reviewable artifacts
- trust policy can determine what may proceed and what must escalate
- quality gates can block weak or risky work
- production launch/write actions can happen under policy
- audit logs can explain what happened and why
- Night Shift can be advanced through the system in practice

## MVP Capabilities

The MVP should include these capabilities at a product level:

- company context for Night Shift
- work request intake
- work packet creation and review
- agent roles or agent sections
- policy and approval records
- typed capability definitions
- production action records
- quality gate records
- artifact registry
- audit trail
- founder review loop

These are product requirements, not current implementation details. React Router and TypeScript are blessed for the web app/control-plane UI, but the exact schemas, services, and remaining UI details are still undecided.

## Production Launch/Write Requirement

The MVP must include real production launch/write capability, but only after the relevant policies, quality gates, capabilities, and audit trail are in place.

Production launch/write examples may include:

- deploying an approved Night Shift change
- publishing an approved production configuration change
- creating or updating production integration configuration
- performing an approved operational write through a typed capability

The exact first production write should be chosen during product and architecture planning.

## Non-Goals Before MVP

The project should not optimize for:

- external customer onboarding
- pricing and packaging
- broad enterprise permissions
- fully generalized company automation
- autonomous legal, tax, accounting, or security conclusions
- exhaustive integrations
- hiding production execution logic in private code
- app scaffolding before stack decisions are resolved

## MVP Acceptance Criteria

MVP readiness requires evidence that:

- Night Shift was advanced through ai-company workflows
- at least one real production launch/write path was completed or safely blocked according to policy
- each meaningful action has intent, context, risk, status, and audit trail
- quality gates ran before production-impacting actions
- founder approvals were requested only when policy required them
- unresolved risks were visible rather than hidden
- secrets, credentials, customer data, and private datasets were not committed
