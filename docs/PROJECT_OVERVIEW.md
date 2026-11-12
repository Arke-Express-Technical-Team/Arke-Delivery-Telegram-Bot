# Project overview and architecture

## Confirmed project goal

Arke Delivery Telegram Bot is intended to help users select a **pickup** location and **drop-off** location, show a delivery cost based on the chosen route, and support the delivery journey from pickup to drop-off.

The repository's initial README establishes this goal. It does **not** establish that working features, a particular programming language, or a production deployment already exist. This document distinguishes proposed design from approved implementation.

## Proposed user journey (not yet verified as implemented)

1. User starts the Telegram bot and is presented with clear instructions.
2. User selects or enters an available pickup location.
3. User selects or enters a supported drop-off location.
4. Bot shows the route summary and quoted price **before** requesting confirmation.
5. User confirms or cancels.
6. The delivery request is created and progresses through the operational stages agreed with the business team.
7. Users receive relevant status updates until completion or cancellation.

Exact supported locations, serviceability checks, payment handling, pickup/drop-off verification, and delivery actors must be agreed before production development. Do not imply a request is accepted or paid until the relevant system has confirmed it.

## Proposed logical components

```text
Telegram user
     |
     v
Telegram bot interface (commands, messages, selections)
     |
     v
Conversation / request orchestration
     |                     |
     v                     v
Location validation    Pricing service
     |                     |
     +----------+----------+
                |
                v
        Delivery request / status service
                |
                v
     Persistence and operational integrations
```

These are conceptual responsibilities, **not existing folders or services**. Prefer a simple modular design for an MVP, then split components only when justified.

### Responsibilities
- **Bot interface:** command handlers, user prompts, input validation, accessible error messages.
- **Location management:** supported pickup and drop-off choices, validation, change of selection.
- **Pricing:** one approved source of truth for the quoted cost; handle unsupported routes and missing rate data explicitly.
- **Delivery lifecycle:** confirmed business states, authorized status changes, failure/cancellation handling.
- **Persistence:** reliable request and status records; avoid collecting unnecessary personal data.
- **Observability/tests:** structured diagnostics without exposing tokens or personal information; deterministic tests for pricing and lifecycle behavior.

## Decisions required before implementation

| Area | Decision to record |
| --- | --- |
| Runtime and Telegram framework | Language, version, framework and supported deployment environment |
| Data storage | Database choice, schema, retention and backup expectations |
| Locations | Allowed locations, display names and who maintains them |
| Price calculation | Rate table or distance logic, currency, rounding, exceptional charges and approval owner |
| Operations | Who accepts deliveries, permissions, and supported status transitions |
| Payments | Whether payments are in scope; provider and payment confirmation rules |
| Deployment | Hosting, secrets, environments and monitoring |
| Testing | Unit/integration test tooling and acceptance test environment |

Do not invent dependency installation commands until the stack is chosen and a corresponding manifest has been committed. Record approved decisions in this file or a dedicated architecture decision record.

## Suggested acceptance criteria for the first MVP

- A user can select valid pickup and drop-off locations and correct a selection.
- The bot gives a consistent, explainable quote for a configured route.
- Unsupported locations or unpriced routes yield an explicit message rather than a fabricated cost.
- A request is only submitted after clear user confirmation.
- Operational states and changes are recorded consistently.
- Secrets stay outside the repository; core behavior has repeatable automated tests.

These are **proposals for review**, not promises that these features have been delivered.

## Documentation index

- [Contributing](CONTRIBUTING.md)
- [Git naming and review conventions](GIT_CONVENTIONS.md)
- [Task delegation](TASK_DELEGATION.md)
- [Task implementation guides](TASK_GUIDES.md)
