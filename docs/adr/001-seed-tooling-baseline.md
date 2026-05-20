# ADR 001: Seed Tooling Baseline

Status: Blessed

Date: 2026-05-19

Owner: founder

Decision type: stack

## Context

The repository is in the seed phase and needs enough project tooling to support disciplined documentation, future stack decisions, and public-safe collaboration.

The project should not accidentally adopt GitHub Actions, GitHub Issues, dotenv files, ad hoc task commands, ad hoc formatting, ad hoc dependency maintenance, ad hoc secret scanning, ad hoc stacked PR workflows, or ad hoc release management while the broader application stack remains undecided.

## Decision

Bless these seed-phase tools:

- Buildkite for CI.
- Plane for issue and project tracking.
- mise for task running, tool version pinning, and committed tool lockfiles.
- Renovate for automated dependency maintenance.
- fnox for secrets management.
- Infisical as the fnox remote provider when encrypted in-repo secrets are insufficient.
- Infisical for secret scanning.
- pitchfork for process and daemon management.
- hk for git hooks and project lint/check orchestration.
- dprint for formatting orchestration.
- cargo-binstall for accelerating cargo-installed seed CLIs.
- Aviator CLI for stacked PRs.
- Aviator MergeQueue for merge queue.
- Aviator Releases for release management.
- communique for release notes unless superseded later.

Reject these for now:

- GitHub Actions.
- GitHub Issues.
- committed `.env` files.
- committed `.env.example` files.

Pin initial tool versions in `mise.toml`:

- `fnox@1.25.1`
- `infisical@0.43.85`
- `rust@1.88.0` for cargo-installed seed tools only
- `dprint@0.54.0`
- `cargo-binstall@1.19.1`
- `github:aviator-co/av@0.1.35`
- `cargo:hk@1.45.0`
- `cargo:pitchfork-cli@2.11.0`
- `cargo:communique@1.1.3`

The cargo backend is used for hk, pitchfork, and communique because their GitHub release assets do not currently support every local development platform used by this repository.

The Rust and cargo-binstall pins are tooling dependencies for those cargo-installed CLIs. They do not bless Rust as an application language.

Enable `mise.lock` and set mise's minimum release age to three days. Commit `mise.lock` so local development and CI resolve the same seed tools. Disable mise task auto-install so repository tasks do not try to install unrelated global tools. Configure Buildkite to ignore agent-global mise config.

## Rationale

These decisions establish the workflow substrate without prematurely choosing the application stack.

Buildkite keeps CI out of GitHub Actions. Plane keeps work tracking out of GitHub Issues. mise makes tool and task entrypoints explicit. `mise.lock` makes seed tooling reproducible. Renovate gives dependency updates an explicit owner. fnox avoids dotenv-based secret drift. Infisical gives fnox a remote-provider path when encrypted in-repo secrets are not enough and provides secret scanning. pitchfork gives the project a blessed path for local daemon management once services exist. hk gives the project a single hook/check entrypoint. dprint gives the project formatting orchestration without choosing language-specific formatters too early. cargo-binstall accelerates cargo-installed seed CLI setup without blessing Rust for application code. Aviator gives the project stacked PRs, merge queue, and release management. communique gives the project a release-note path that can use repository context without hand-written release churn.

## Options Considered

GitHub Actions: rejected for now because the founder wants Buildkite.

GitHub Issues: rejected for now because the founder wants Plane and wants GitHub Issues disabled.

Dotenv examples: rejected because the founder wants no `.env` files in the repo and wants fnox as the secrets path.

Ad hoc shell scripts: rejected for now because mise should be the task entrypoint.

Ad hoc formatting: rejected for now because dprint should orchestrate formatting.

Ad hoc dependency update scripts: rejected for now because Renovate should manage automated dependency updates.

Ad hoc secret scanning: rejected for now because Infisical should scan for committed secrets.

Ad hoc merge and release workflows: rejected for now because Aviator should handle stacked PRs, merge queue, and release management.

## Consequences

Positive consequences:

- CI, tasks, hooks, secrets, secret scanning, dependency maintenance, daemon management, issue tracking, formatting, stacked PRs, merge queue, release management, and release notes have explicit seed-phase owners.
- Future agents should not add GitHub Actions, GitHub Issues templates, or dotenv examples by default.
- The repository can keep app-stack decisions TBD while still having project hygiene.

Negative consequences:

- Buildkite must be configured outside this repository.
- GitHub Issues must remain disabled in repository settings.
- Plane must be configured outside this repository.
- Aviator must be installed/configured outside this repository.
- Buildkite should exclude Aviator temporary `mq-tmp-*` branches with `!mq-tmp-*`.
- Aviator Releases needs Buildkite API credentials and release project configuration outside this repository.
- Infisical hosted repository scanning and remote secret projects must be configured outside this repository.
- Renovate must be installed or run outside this repository.
- Public contributor intake needs a future decision because GitHub Issues are not used.
- `fnox.toml` and `pitchfork.toml` are intentionally deferred until real secrets or daemons exist.
- dprint includes docs/config formatters, but language-specific plugins are intentionally deferred until language decisions are blessed.

## Revisit Trigger

Revisit this decision if any blessed tool blocks local development, CI, release, code review, dependency maintenance, secret scanning, or public contribution workflows, or if the project changes its policy on GitHub Issues, GitHub Actions, dotenv files, Aviator, Plane, Renovate, Infisical, or dprint.

## Related Documents

- `README.md`
- `AGENTS.md`
- `SECURITY.md`
- `CONTRIBUTING.md`
- `docs/07-decision-system.md`
- `docs/08-stack-decision-backlog.md`
- `docs/09-build-sequence.md`
- `docs/10-code-review-methodology.md`
- `.aviator/config.yml`
- `dprint.json`
- `mise.lock`
- `renovate.json`
