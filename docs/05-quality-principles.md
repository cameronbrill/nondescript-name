# Quality Principles

ai-company must optimize for fewer, better artifacts and safer execution, not more output.

The product should reject generic AI slop even when it looks superficially complete.

## Quality Bar

Work is high quality when it is:

- specific to company context
- scoped clearly
- explicit about non-goals
- technically feasible
- operationally safe
- testable
- reviewable
- maintainable
- tied to evidence
- clear about risk
- useful for implementation or decision-making

## Definition Of AI Slop

An output is AI slop if it is:

- generic
- unactionable
- internally inconsistent
- detached from company context
- architecturally vague
- aesthetically careless
- not testable
- missing constraints
- missing risk boundaries
- full of unsupported claims
- optimized for looking complete instead of being useful

## Quality Gates

Every significant work packet should eventually include quality gates for:

- scope clarity
- non-goals
- acceptance criteria
- technical feasibility
- trust and risk review
- security and privacy review when relevant
- test plan
- implementation usefulness
- production readiness when relevant
- audit completeness

The exact automated and manual quality gates are future decisions.

## Engineering Quality

When application code begins, engineering quality should include:

- type checks
- tests
- linting
- formatting
- code review
- schema validation where applicable
- migration safety where applicable
- dependency review
- secret scanning
- production action safeguards
- integration mocks before live credentials

Seed-phase tooling has blessed hk for project checks, dprint for formatting orchestration, Infisical for secret scanning, and Renovate for dependency maintenance. Language-specific tools and code review methodology remain TBD until the stack decision process is complete.

## Code Review

Code review methodology and tooling require a dedicated decision.

Until that decision is blessed, use `docs/10-code-review-methodology.md` as the placeholder. Production-impacting changes require founder review before MVP. AI-assisted review may help, but it must not be the only review mechanism for high-risk changes.

## Product Quality

The product should produce founder leverage, not founder homework.

A good morning review should tell the founder:

- what changed
- why it changed
- what evidence supports it
- what was blocked
- what needs approval
- what risks remain
- what the system recommends next

## Night Shift Quality Standard

Night Shift is the first proof case.

If ai-company cannot produce high-quality, context-aware, operationally safe work for Night Shift, it should not claim readiness for broader users.
