# Product Constitution

This document defines the durable product constraints for ai-company.

## What We Are Building

ai-company is an open-source AI operating system for building, launching, and operating a solo SaaS company.

The product should let a founder delegate meaningful company work to agents while preserving scrutiny, quality, auditability, and approval-by-policy.

## North Star

AI should be able to build and operate meaningful parts of a company while the founder sleeps.

This is not permission for invisible automation. The system must make autonomy safer through explicit policies, typed capabilities, quality gates, approval-by-exception, and complete audit trails.

## Target User

The initial target user is a technical solo SaaS founder.

This founder understands software production, source control, CI, deploy previews, logs, incidents, integrations, and approval tradeoffs. The product can expand later, but the first version should not hide technical reality from the founder.

## Core Promise

Give a solo founder production-grade company leverage without quality churn.

## Product Beliefs

1. Autonomy is only useful when the founder can trust what happened.
2. Agents should act through explicit capabilities, not raw uncontrolled access.
3. The system should optimize for approval-by-policy, not approval-for-every-action.
4. The best founder experience is not constant chat. It is reliable overnight progress and a clear morning review.
5. Production launch/write capability is part of the product, not a postscript.
6. Auditability is a core feature, not a compliance afterthought.
7. Quality systems are part of the moat.
8. The project should be public by default and safe because of its architecture, not because critical behavior is hidden.
9. Recommended defaults should not become vendor lock-in.

## What We Are Not Building

ai-company is not:

- a generic chatbot
- a low-quality code generator
- a planning-only productivity app
- a fully unbounded autonomous company-in-a-box
- a system that hides production risk from the founder
- a replacement for legal, tax, accounting, security, or compliance professionals in high-risk decisions
- a secretive closed execution engine wrapped in open-source docs

## Product Pillars

1. Governed autonomy.
2. High-quality execution.
3. Explicit trust boundaries.
4. Complete auditability.
5. Typed integration capabilities.
6. Persistent company context.
7. Approval-by-policy.
8. Public-by-default implementation.
9. Dogfood before claims.
10. Maintenance beats one-off generation.
11. Recommended defaults with swappable integrations.

## Core Vocabulary

Company: the business context the system is helping build and operate.

Company context: structured information about the company, product, users, architecture, operations, risks, decisions, and current work.

Work request: a founder's request for meaningful company work.

Work packet: a governed unit of work that includes intent, scope, proposed actions, artifacts, approvals, quality gates, and audit trail.

Agent action: a proposed, staged, or executed action by an agent.

Capability: a typed ability exposed to an agent, usually through an integration or internal system. External capabilities should be implemented through provider adapters rather than hard-coded vendor paths.

Policy: a standing rule that determines what agents may do, what they must escalate, and what they must log.

Approval: a founder decision that permits, rejects, or modifies an action outside already-approved policy.

Quality gate: a required check before work can advance.

Audit trail: the durable record of intent, context, action, status, result, and approvals.

## Current Constraints

This repository is in the seed phase.

Do not scaffold application code until the stack decision backlog has been reviewed and enough choices are explicitly blessed to support implementation.

Do not turn unresolved architecture or product questions into accidental defaults.
