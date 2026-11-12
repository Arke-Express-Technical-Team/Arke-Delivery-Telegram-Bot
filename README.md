# Arke Delivery Telegram Bot

A planned Telegram-based delivery bot for **Arke Express**. Users will select pickup and drop-off locations, receive a delivery quote based on those locations, and follow the delivery process through its supported stages.

> **Project status:** Early-stage repository. The project goal is documented, but the runtime, dependencies, pricing policy, operational rules and actual implemented features must be confirmed before setup or deployment instructions can be provided.

## Project scope

The proposed MVP includes:
- Pickup and drop-off location selection and validation.
- Delivery cost quotation using **approved** pricing rules.
- Explicit confirmation before creating a delivery request.
- A clearly defined delivery request/status lifecycle.
- Tests, operational safeguards and documentation.

These are planned capabilities, **not a claim that they are currently implemented**. See [project overview](docs/PROJECT_OVERVIEW.md) for open decisions and a proposed architecture.

## Get started as a contributor

1. Accept your collaborator invitation if applicable.
2. Clone the repository:
   ```bash
   git clone https://github.com/Arke-Express-Technical-Team/Arke-Delivery-Telegram-Bot.git
   cd Arke-Delivery-Telegram-Bot
   ```
3. Review your assigned GitHub issue and the documentation linked below.
4. Start from the latest `main` and create a dedicated branch:
   ```bash
   git switch main
   git pull --ff-only origin main
   git switch -c feature/short-task-description
   ```
5. Implement the agreed scope, run available tests, commit and push:
   ```bash
   git add <paths-you-changed>
   git commit -m "feat: describe your change"
   git push -u origin feature/short-task-description
   ```
6. Open a pull request targeting `main` with a **summary, linked task, test evidence and known limitations**. Address review feedback and follow branch protection requirements.

**Important:** `git checkout -m` is **not** how to create a new branch. Use `git switch -c` or `git checkout -b`. Never commit credentials or real Telegram bot tokens.

The project does not yet document a confirmed application stack or installation command. Task owners must not assume a language or framework before team approval.

## Team documentation

| Document | Purpose |
| --- | --- |
| [Contributing guide](docs/CONTRIBUTING.md) | Clone, branch, implement, test and submit PRs |
| [Project overview and architecture](docs/PROJECT_OVERVIEW.md) | Goal, proposed components, MVP scope and pending decisions |
| [Git conventions](docs/GIT_CONVENTIONS.md) | Branch names, Conventional Commits and PR standards |
| [Task delegation](docs/TASK_DELEGATION.md) | Roles, issue format, ownership, deadlines and communication |
| [Task implementation guides](docs/TASK_GUIDES.md) | Proposed task breakdown, dependencies and acceptance criteria |

## Collaboration principles

Each task should have a documented scope, owner, reviewer, deadline and acceptance criteria in GitHub Issues or a project board. Raise blockers early; respectful questions and constructive code review are part of the team's learning process. Changes should go through dedicated branches and reviewed PRs rather than direct pushes to `main`.
