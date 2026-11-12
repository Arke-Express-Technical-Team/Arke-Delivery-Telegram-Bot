# Task delegation and ownership

This document defines how work is assigned and tracked. **No individual assignments or deadlines have yet been confirmed in this repository**, so none are invented here.

## Responsibilities

- **Technical lead:** clarify scope and acceptance criteria, prioritize tasks, assign a single directly responsible owner, resolve cross-task dependencies, review PRs or coordinate reviewers, and communicate deadline changes.
- **Task owner:** review requirements, flag ambiguity early, implement on a separate branch, test, document, and open a PR with evidence.
- **Reviewer:** evaluate correctness, maintainability, security, scope and tests; leave actionable feedback and confirm fixes.
- **All contributors:** communicate blockers and handoffs respectfully and proactively.

The technical lead should encourage questions and learning, especially for contributors new to Git/GitHub or Telegram bot development. Strict timelines should be realistic, agreed in advance, and adjusted transparently when blocked by dependencies.

## Source of truth: GitHub issues or project board

Create one issue for each independently reviewable task. Use labels such as `feature`, `bug`, `documentation`, `blocked`, and priority labels if adopted by the team. Record actual assignees and due dates in the issue/project board; do not silently amend assignments in prose.

Suggested issue template:

```md
## Objective
What outcome is needed, and why?

## Scope
Included:
- ...
Excluded:
- ...

## Dependencies
- ...

## Acceptance criteria
- [ ] ...
- [ ] ...

## Implementation notes
Suggested approach; do not overconstrain design.

## Testing and documentation
- ...

## Owner / reviewer / deadline
Owner: TBD
Reviewer: TBD
Due: TBD (timezone specified)

## Status / blockers
Not started
```

## Proposed initial workstreams (not assigned)

| Workstream | Deliverable | Prerequisites | Owner | Due date |
| --- | --- | --- | --- | --- |
| Foundation | Agree stack, environment setup, bootable bot and basic tests | Team architecture decision | TBD | TBD |
| User interaction | Pickup and drop-off selection flow with validation | Bot foundation; approved locations | TBD | TBD |
| Pricing | Quotation logic with approved rate rules and test cases | Pricing policy and location catalog | TBD | TBD |
| Delivery lifecycle | Confirmed request creation and status transitions | Business rules; persistence decision | TBD | TBD |
| Quality and integration | CI, integration tests, operational documentation | Other workstreams and test environment | TBD | TBD |

Workstreams can be split into smaller issues to match team capacity. Record dependencies to avoid parallel work implementing conflicting interfaces.

## Suggested workflow

1. Lead creates and explains an issue with objective, owner, deadline and acceptance criteria.
2. Owner acknowledges it and identifies blockers or missing decisions.
3. Owner works on a descriptive feature branch, keeping the issue updated.
4. Owner tests and opens a PR linked to the issue.
5. Reviewer gives specific feedback; owner revises if needed.
6. Merge occurs only after the repository's required checks and review policies are satisfied.
7. Lead verifies the outcome against acceptance criteria and updates the project board.

### Communication norms

Post a concise update when a milestone completes, a dependency changes, or a blocker appears. Include what happened, impact and help needed. Do not equate learning questions with poor performance; use reviews as opportunities to grow.
