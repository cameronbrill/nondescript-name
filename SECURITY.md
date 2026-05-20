# Security Policy

ai-company is public by default, but public does not mean careless.

## Reporting Security Issues

Do not open public issues for vulnerabilities that could expose users, credentials, infrastructure, or production systems.

Until a formal private disclosure channel exists, contact the repository owner directly.

## Public Repository Rules

Never commit:

- API keys
- OAuth secrets
- provider tokens
- private keys
- production credentials
- customer data
- production incident data
- proprietary or private eval datasets
- `.env` files
- `.env.example` files
- logs containing secrets or user data

## Secrets Management

fnox is the blessed secrets management tool for this repository.

Infisical is the blessed fnox remote provider when encrypted in-repo secrets are not sufficient.

Do not use committed dotenv files as the secrets interface. If a future task needs secret names, document them through fnox-oriented configuration or docs without committing secret values.

## Secret Scanning

Infisical is the blessed secret scanning tool for this repository.

Run `mise run secret-scan` when a change could expose secrets, credentials, tokens, private keys, customer data, private datasets, or logs.

## Security Philosophy

The project is intended to be 100% open source, including production execution logic and commercial connectors.

Safety must come from:

- least-privilege credentials
- explicit capability boundaries
- approval-by-policy
- audit logs
- quality gates
- tests
- code review
- environment isolation
- secret hygiene

Safety must not depend on hiding the code that performs production actions.

## Current Phase

This repository is in the seed phase and should not contain live integration code or production credentials.

GitHub Issues are disabled for this repository. Do not report security issues through GitHub Issues.
