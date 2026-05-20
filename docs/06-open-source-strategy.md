# Open-Source Strategy

ai-company is public by default.

The goal is for 100% of ai-company to be open source, including production execution logic and commercial connectors.

## Principle

Security and trust should come from design, not obscurity.

Public code should be safe because it uses explicit policies, least-privilege credentials, typed capabilities, quality gates, tests, review, and audit trails.

## What Should Be Public

The repository should include:

- product doctrine
- architecture docs
- decision records
- core application code when implementation begins
- production execution logic
- commercial connector code
- capability definitions
- policy logic
- mock integrations
- tests
- examples that do not expose sensitive data
- public-safe audit examples

## What Must Not Be Public

The repository must not include:

- secrets
- credentials
- private keys
- provider tokens
- customer data
- private/internal datasets
- proprietary customer artifacts
- production incident data that identifies customers or systems
- unredacted logs containing sensitive information
- environment files with real values

## Production Execution Logic

Production execution logic means code that can perform real-world actions against live systems, such as deploys, configuration changes, integration writes, or operational remediations.

In this project, that logic should be open source.

The safety boundary should be credentials, permissions, policy, environment isolation, review, and runtime controls, not hidden source code.

## Commercial Connectors

Commercial connectors are integrations with production services such as source control, hosting, observability, incident tools, communication tools, billing systems, and customer operations systems.

Connector code should be open source. Real credentials, customer configuration, and private operational data must remain outside the repo.

Connectors should be swappable provider adapters behind typed capabilities. Blessed-path vendors are recommended defaults for setup and dogfooding, not exclusive product dependencies.

Examples: issue tracking may recommend Plane while supporting Linear, Jira, GitHub Issues, or existing user accounts. Code forge integrations may recommend Codeberg or Forgejo while supporting GitHub and GitLab.

## Public Evidence

Because the project is dogfood-driven, public evidence matters.

The project should publish public-safe examples of work packets, audit records, policies, capability definitions, quality gates, and Night Shift dogfood outcomes.

Evidence must be redacted or synthetic when needed to protect secrets, customer data, private infrastructure, or incident details.

## License

The seed repository uses the MIT License.

If the license choice needs to change, record the decision in the decision system and update the repository consistently.
