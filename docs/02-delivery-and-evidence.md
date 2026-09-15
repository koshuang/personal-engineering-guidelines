# Delivery and Evidence

## Delivery mode should match the question

Use the smallest delivery mode that can produce credible evidence:

- **Prototype** — explore interaction, shape, or feasibility; disposable is acceptable.
- **PoC** — prove a specific technical or integration assumption.
- **MVP** — deliver the smallest usable product that can test value with real usage.
- **Pilot** — validate behavior and operations under bounded real-world use.
- **Production** — optimize for repeatability, observability, recoverability, and ongoing ownership.

Do not apply production ceremony to a disposable experiment unless the risk justifies it. Do not quietly ship prototype assumptions into durable production without re-evaluating them.

## Testing strategy

Choose tests according to the failure mode:

- domain/business behavior → fast deterministic tests;
- persistence and migration semantics → real database integration tests when meaningful;
- API contracts → contract/HTTP-level tests;
- browser behavior → browser/E2E/smoke validation;
- deployment → artifact/release test plus post-deploy read-back;
- scheduled automation → replay/idempotency/deduplication/failure-recovery tests.

Prefer a smaller number of meaningful tests over duplicated tests that prove the same thing.

## CI baseline

For an active software project, CI SHOULD verify the checks that are cheap and deterministic enough to run repeatedly, such as:

- test suite;
- type/static analysis where applicable;
- lint/format policy when it catches real defects or coordination friction;
- build/package integrity;
- migration/schema validation when relevant;
- artifact creation for deployable software.

The exact toolchain is project-specific.

## Release baseline

When a project is deployed, prefer build-once delivery:

`source -> CI verification -> immutable artifact/image -> deployment -> runtime verification`

Avoid rebuilding application code on the production host when practical. Keep a clear relationship between source revision and deployed artifact.

Production deployment may be manual while a project is young. Automation should increase when it reduces operational risk and recurring effort rather than simply because automation is possible.

## Completion evidence

Before declaring material work complete, answer:

1. What outcome/acceptance criteria were expected?
2. What checks actually ran?
3. What did they observe?
4. If runtime behavior matters, was the real path exercised?
5. If persistent data or external side effects are involved, is retry/rollback/recovery understood?
6. Is important evidence durable and discoverable later?

## Operational automation

Scheduled jobs and autonomous agents should be designed for:

- bounded execution;
- idempotency or explicit deduplication;
- checkpoint/recovery after interruption;
- observable success/failure;
- explicit cost and permission boundaries;
- an objective closure condition.

Never manufacture work merely to keep an automation busy.
