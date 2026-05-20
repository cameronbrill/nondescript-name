# ADR 002: Vendor Integration Abstraction

Status: Blessed

Date: 2026-05-19

Owner: founder

Decision type: architecture

## Context

ai-company will connect to external systems such as issue trackers, code forges, observability tools, incident tools, communication tools, billing systems, hosting providers, and customer systems.

The repository also has blessed seed tools for its own work, such as Plane for project tracking and Buildkite for CI. Those choices should make this repository coherent, but they must not accidentally become hard product dependencies for users.

The product should recommend strong defaults while allowing founders to use their existing accounts and preferred tools.

## Decision

Bless a vendor integration abstraction rule for the product.

Product integrations must be built around abstract capabilities and provider adapters. A blessed path is a recommended default, not a hard product dependency, unless a later ADR explicitly narrows a product surface.

Examples:

- Issue tracking should recommend Plane, but the product should allow Linear, Jira, GitHub Issues, or another provider through the same issue-tracking capability.
- Code forge and source control should recommend Codeberg or Forgejo where appropriate, but the product should support GitHub and GitLab through the same code-forge capability.
- Existing user accounts should be first-class. Users should not need to migrate tools merely to use ai-company unless a workflow genuinely requires it.

Agents should act through typed capabilities, not raw vendor SDKs. Provider adapters bind those capabilities to concrete external services under policy, permission, audit, and test boundaries.

## Rationale

The product exists to run governed company work, not to force a founder into a single SaaS stack.

Recommended defaults reduce setup friction and give the project a path for dogfooding. Abstractions preserve user choice, reduce lock-in, make public connector code safer to review, and keep policy enforcement consistent across providers.

This also keeps ai-company honest about its open-source posture. If production execution logic and commercial connectors are public, then connector boundaries should be explicit and replaceable.

## Options Considered

Hard-code blessed providers: rejected because it would confuse repository tooling choices with product requirements and make adoption harder for founders with existing systems.

Provider-neutral abstractions only, with no recommended defaults: rejected because it would slow dogfooding and make initial setup too vague.

Recommended defaults plus provider adapters: blessed because it balances opinionated setup with tool choice.

## Consequences

Positive consequences:

- Users can keep existing accounts and workflows.
- Connector work has a clear boundary between capability contracts and vendor APIs.
- Policy, approval, audit, and quality gates can be applied consistently across providers.
- The product can dogfood recommended defaults without pretending they are universal requirements.

Negative consequences:

- Connector design takes more discipline than direct vendor SDK calls.
- Tests need shared contract coverage plus provider-specific adapter coverage.
- Some provider features may not map cleanly to the common capability contract.

## Revisit Trigger

Revisit this decision if abstraction prevents MVP proof, if a provider-specific feature becomes product-defining, or if maintaining multiple adapters blocks core product progress.

## Related Documents

- `README.md`
- `AGENTS.md`
- `docs/00-product-constitution.md`
- `docs/04-trust-and-autonomy-principles.md`
- `docs/06-open-source-strategy.md`
- `docs/08-stack-decision-backlog.md`
