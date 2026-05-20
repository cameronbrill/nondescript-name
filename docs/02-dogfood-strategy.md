# Dogfood Strategy

Dogfooding is the primary proof mechanism for ai-company.

The product should not claim to build or operate companies until it has done so for real under its own constraints.

## Dogfood Companies

Night Shift is the first canonical customer and product dogfood case.

Night Shift is the AI first responder for production incidents. It is a concrete SaaS product with real operational risk, which makes it a strong test case for trust, quality, integrations, and production execution.

ai-company is also a dogfood company. However, ai-company requires tighter founder oversight before MVP because mistakes in the operating system can affect all future work.

## Why Night Shift First

Night Shift forces the system to reason about:

- production incidents
- alert context
- integration permissions
- escalation policies
- safe read-only investigation
- approval-gated remediation
- audit logs
- customer trust
- launch readiness
- reliability expectations

This makes Night Shift a better dogfood case than a toy application.

## MVP Dogfood Claim

The MVP is ready only when Night Shift has been built, launched, and operated through ai-company workflows that include real production launch/write capability under explicit trust policies.

Planning alone is not enough.

## Required Dogfood Evidence

Before claiming MVP readiness, the repo should contain public evidence that ai-company supported Night Shift through:

- company context capture
- work request intake
- work packet creation
- policy definition
- capability definition
- artifact generation or management
- implementation planning
- staged execution
- quality gate results
- approval records
- production launch/write actions
- audit logs or redacted audit examples
- post-action review

Sensitive credentials, customer data, production secrets, and private datasets must not be included in this evidence.

## Oversight Difference

Night Shift is the first external product dogfood case.

ai-company is self-dogfood with stricter controls. Before MVP, founder approval should be required more often for changes to ai-company doctrine, policies, execution logic, stack, and production behavior.

## Dogfood Failure Conditions

The dogfood process is failing if:

- agents produce generic artifacts detached from company context
- production actions happen without clear policy or audit trail
- the founder cannot reconstruct what happened and why
- quality gates are skipped for speed
- stack or architecture decisions are made casually
- Night Shift becomes a side quest instead of the canonical proof case
