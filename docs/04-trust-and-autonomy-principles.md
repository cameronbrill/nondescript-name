# Trust And Autonomy Principles

Trust is the central product problem.

ai-company should enable real autonomy, including production launch/write actions, without making those actions invisible, unbounded, or unauditable.

## Core Principle

Use approval-by-policy, not approval-for-everything.

The founder should define standing policies that let agents act inside approved boundaries. Agents should escalate only when an action is outside policy, ambiguous, high-risk, irreversible, or production-impacting beyond the approved scope.

## What Approval-By-Policy Means

Approval-by-policy means the founder approves classes of action ahead of time.

Examples:

- agents may create draft specs without approval
- agents may open pull requests in approved repositories without approval
- agents may deploy preview environments after tests pass
- agents may post internal summaries to approved channels
- agents may not deploy production unless the relevant policy permits it
- agents may not change billing, secrets, or production data without explicit policy and audit requirements

The exact policy language and engine are future technical decisions.

## Vendor Integration Abstraction

Agents should act through abstract capabilities, not raw vendor SDKs.

A capability should describe the action the system is allowed to take, such as creating an issue, opening a pull request, reading an alert, or posting an internal summary. Provider adapters should bind that capability to a concrete service such as Plane, Linear, Jira, GitHub Issues, Codeberg, Forgejo, GitHub, GitLab, Slack, or another provider.

Recommended defaults are allowed, but they should not erase user choice. Policy, permissions, audit records, and quality gates should attach to the capability and adapter boundary.

## Action Risk Levels

All meaningful agent actions should be assessed by risk.

Low risk: read-only, draft-only, easily reversible, internal, non-production.

Medium risk: changes shared artifacts, opens pull requests, creates tasks, posts internal updates, modifies non-production environments.

High risk: affects production, users, money, security, trust, customer communication, billing, infrastructure, or external systems.

Restricted: legal conclusions, tax/accounting conclusions, irreversible deletion, secret exposure, customer refunds, contract signing, security attestations, or other actions the project explicitly forbids agents from performing autonomously.

## Required Action Envelope

Every meaningful agent action should eventually include:

- intent
- triggering request
- context used
- capability used
- proposed or executed change
- risk level
- policy basis
- approval requirement
- expected impact
- rollback or mitigation plan when applicable
- status
- result
- audit record

The exact schema is not yet decided.

## Production Actions

Production launch/write capability is required for MVP, but production actions must be governed more strictly than planning or staging actions.

Before any production-impacting action, the system should know:

- what policy permits the action
- what quality gates passed
- what artifact or change is being released
- what system will be affected
- what rollback path exists, if any
- what evidence should be captured afterward
- what the founder will see in review

## Sleep Mode

The long-term product should support an overnight operating mode.

Sleep mode does not mean agents can do anything. It means agents can continue approved work, pause on uncertain work, and prepare a morning review without repeatedly interrupting the founder.

## Founder Oversight

Before MVP, founder oversight should be stricter than the eventual product goal.

ai-company changes should require especially high scrutiny because this system defines the rules future agents will use.

## Default Seed-Phase Rule

Until explicit policies and capabilities are implemented, assume production-impacting actions require direct founder approval.

Do not infer permission from ambition.
