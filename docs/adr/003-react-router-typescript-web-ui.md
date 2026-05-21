# ADR 003: React Router And TypeScript For Web UI

Status: Blessed

Date: 2026-05-20

Owner: founder

Decision type: stack

## Context

The repository is in the seed phase and needs enough web stack direction to support a future app scaffold without committing the entire application architecture too early.

ai-company needs a control-plane UI for reviewing agent intent, policy decisions, approvals, audit trails, incidents, and operational status. This UI must not become an unchecked production-action surface. Production-capable actions must remain server-side, go through typed capabilities, policy checks, approval gates, and audit logging.

## Decision

Bless React Router and TypeScript for the web app and control-plane UI.

This decision blesses:

- React Router for the web UI framework and routing foundation.
- TypeScript for the web UI language.
- Server-side handling for production-capable actions.
- Go for company CLIs.
- Deferring Rust as an application language.

This decision rejects Datastar for now because of Pro licensing concerns, Content Security Policy fit, and maturity risk for this project.

This decision does not scaffold app code.

This decision does not bless the backend framework, database, hosting provider, auth provider, policy engine, capability runtime, queue, durable workflow runner, styling system, component library, form library, validation system, realtime transport, test runner, or deployment model. Those remain TBD.

## Rationale

React Router gives the project a mature web UI foundation without forcing the rest of the backend or agent runtime architecture. TypeScript fits the browser UI surface and supports typed UI contracts once the server API and capability boundaries are defined.

The control plane should make risk visible. It should show intent, context, status, approvals, and audit evidence. It should not perform production work directly from client code. Browser interactions may request an action, but production effects must execute on the server through typed capabilities, provider adapters, policy evaluation, approval records, and audit trails.

Go is blessed for company CLIs because it is a strong fit for small operational tools, static binary distribution, startup time, and public contributor ergonomics. This does not require Go for the whole backend.

Rust remains deferred for application code. Current Rust usage exists only to install seed CLIs that are already blessed by ADR 001.

Datastar is rejected for now. Its model is interesting, but Pro licensing concerns, Content Security Policy implications, and project maturity risk make it a poor default for the seed-phase control plane.

## Options Considered

React Router plus TypeScript: blessed because it gives the web UI a stable direction while preserving backend, data, and execution decisions for later ADRs.

htmx/CSS-first: considered because it keeps server-rendered workflows simple and minimizes frontend code. Rejected for now as the default because the Night Shift live incident and agent-run surfaces are likely to need richer client tooling.

Datastar: rejected for now because of Pro licensing concerns, Content Security Policy fit, and maturity risk.

Rust for application code: deferred because the current Rust pin supports seed tooling only and should not become an accidental application-language decision.

Go for company CLIs: blessed because CLIs benefit from simple distribution and operational reliability.

No web stack decision yet: rejected because the future scaffold needs enough direction for the control-plane UI.

## Consequences

Positive consequences:

- The web UI has a blessed framework and language.
- Future scaffold work can avoid reopening the basic control-plane UI choice.
- Production actions remain server-side and governed.
- The project avoids accidentally blessing Rust as an application language.
- The project avoids Datastar risk during the seed phase.

Negative consequences:

- TypeScript becomes part of the application stack for the web UI.
- React Router choices will influence routing, rendering, testing, and deployment shape.
- Backend/API boundaries still need a separate decision before implementation.
- Datastar may need to be reconsidered later if its licensing, Content Security Policy, and maturity concerns materially change.

## Revisit Trigger

Revisit this decision if React Router blocks the control-plane UI, if deployment constraints conflict with the chosen rendering model, if production-action safety cannot be cleanly enforced across the UI/server boundary, or if Datastar's licensing, Content Security Policy, and maturity concerns materially change.

## Related Documents

- `README.md`
- `AGENTS.md`
- `docs/00-product-constitution.md`
- `docs/04-trust-and-autonomy-principles.md`
- `docs/08-stack-decision-backlog.md`
- `docs/09-build-sequence.md`
- `docs/adr/001-seed-tooling-baseline.md`
- `docs/adr/002-vendor-integration-abstraction.md`
