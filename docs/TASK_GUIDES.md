# Task implementation guides (proposed)

These guides are **candidate tasks**, not final assignments or proof that the described modules already exist. The technical lead must approve the stack, business rules, locations, deadlines and owners before converting them into GitHub issues.

## T01 — Establish the Telegram bot foundation

**Goal:** create a reproducible development and test environment.

Prerequisites: select language/framework, package management and supported runtime; decide how bot credentials are supplied securely.

Implementation approach:
1. Record the agreed stack and dependency manifest.
2. Create the minimal bot entry point and a safe `/start` interaction.
3. Provide `.env.example` using placeholders only; exclude real `.env` files.
4. Add setup/run/test instructions and one or more starter automated tests.
5. Add or document a development CI check where feasible.

Acceptance checks:
- A new contributor can follow documented setup without receiving real secrets.
- A test bot can respond to `/start` in a controlled environment.
- Tests run in the documented environment; errors do not leak tokens.
- PR includes setup/test commands and evidence.

## T02 — Pickup and drop-off selection

**Goal:** collect valid pickup and drop-off locations.

Prerequisites: T01; an approved catalog of serviceable locations and selection behavior.

Implementation approach:
1. Define a shared, maintainable location catalog or provider interface.
2. Implement pickup and drop-off prompts and user selection.
3. Validate available routes and support correcting choices.
4. Handle invalid selections, stale messages, abandoned flows and unsupported areas.
5. Separate Telegram presentation from validation logic for testability.

Acceptance checks:
- Valid pickup and drop-off choices are reliably recorded for the active interaction.
- Users can correct a selection before confirmation.
- Invalid/unsupported choices receive helpful feedback.
- Tests cover normal and invalid paths.

## T03 — Delivery price quotation

**Goal:** show a quote based on the selected pickup and drop-off points.

Prerequisites: T02; written approval of currency, rates or distance policy, rounding, applicable fees and missing-route behavior.

Implementation approach:
1. Express pricing rules through a single pricing interface.
2. Represent approved rates/configuration separately from user messages.
3. Reject unsupported or unpriced routes explicitly; **never fabricate a price**.
4. Return a structured quote and present it clearly to users before confirmation.
5. Test representative routes, invalid routes, boundary conditions and rounding.

Acceptance checks:
- Approved input routes produce expected quotes against agreed fixtures.
- Unsupported routes cannot silently produce arbitrary costs.
- Changing selections refreshes the displayed quote.
- Displayed prices and test expectations use the agreed currency and precision.

## T04 — Delivery request and status lifecycle

**Goal:** submit confirmed requests and manage operational updates.

Prerequisites: T01–T03; approved persistence, user roles, operational states and permission rules.

Implementation approach:
1. Agree on request fields and minimize retained personal data.
2. Define valid states, transitions and which roles may trigger them.
3. Create a request only after the user explicitly confirms the quote.
4. Persist transitions consistently; guard against duplicate callbacks/retries.
5. Communicate status and failure/cancellation behavior clearly.

Acceptance checks:
- No request is created by simply requesting a quote.
- Invalid or unauthorized transitions are rejected.
- Duplicate confirmation messages do not cause unintended duplicate requests.
- Tests cover successful completion, cancellation, failure and retries as applicable.

## T05 — Quality, deployment readiness and handoff

**Goal:** make the project reviewable and operable by the team.

Prerequisites: implemented tasks and agreed hosting/operational requirements.

Implementation approach:
1. Add automated quality checks aligned with the approved stack.
2. Verify integration between selection, pricing and delivery lifecycle.
3. Document configuration, deployment procedure, rollback and operational troubleshooting.
4. Review permission boundaries, secret handling, logging, input validation and data retention.
5. Run an end-to-end scenario with a controlled test bot, recording results.

Acceptance checks:
- Required test suite and CI checks pass.
- Setup and deployment instructions match actual code and environment.
- Sensitive configuration is not committed to Git.
- Handoff documentation identifies current limitations and support ownership.

## Definition of done (every task)

- Scope and acceptance criteria agreed.
- Focused branch and descriptive commits.
- Automated tests or explicit rationale if unavailable, plus manual test evidence.
- Clear PR summary, issue reference, tests and limitations.
- Reviewer feedback resolved and required GitHub checks satisfied.
- Documentation updated when external behavior or setup changes.

See [task delegation](TASK_DELEGATION.md) for assignment procedures and [contributing](CONTRIBUTING.md) for the Git workflow.
