# Code Review Methodology

This document is a placeholder for a dedicated code review methodology and tooling decision.

## Status

TBD.

The project needs a deliberate code review methodology before application code, stacked PR workflows, or production-write workflows become routine.

## Initial Stance

Before MVP, founder review is required for production-impacting changes.

Automated checks are necessary but not sufficient. AI-assisted review may help, but it must not be the only review mechanism for changes that affect production, users, money, security, trust, policy, or agent execution.

## Decisions To Make

- pull request review policy
- stacked PR review flow with Aviator CLI
- merge queue requirements with Aviator MergeQueue
- human review expectations before MVP
- AI-assisted review tooling
- security review gates
- architecture review gates
- review checklist format
- required checks before merge
- review standards for production-write paths
- review standards for connector and capability changes

## Current Workflow Constraints

- Plane is the issue and project tracker.
- Aviator CLI is the stacked PR workflow.
- Aviator MergeQueue is the merge queue.
- Buildkite is the CI system.
- hk runs project checks.
- dprint orchestrates formatting.
- Renovate handles automated dependency maintenance.
- Infisical handles secret scanning.
- GitHub Issues and GitHub Actions are rejected for now.

## Review Principle

Review should protect trust boundaries, quality, and production safety without turning every small change into founder approval theater.
