# Evidence Checklist

Use this when a task, release, migration, automation, or agent run is about to be declared complete. Evidence should match the claim; skip layers that are irrelevant.

## Claim

- What outcome is being claimed?
- Which acceptance criteria or failure mode matter?

## Evidence by layer

### Code / behavior

- [ ] Relevant behavior tests passed.
- [ ] Static/type/lint/build checks passed where applicable.
- [ ] The change is scoped and reviewable.

### Integration

- [ ] Real database semantics were exercised when persistence behavior matters.
- [ ] Real API/HTTP contract was exercised when transport behavior matters.
- [ ] Browser/E2E evidence exists when user-visible behavior matters.
- [ ] External integration failure behavior is understood.

### Delivery

- [ ] The verified source revision maps to the artifact or deployment.
- [ ] Required CI checks are complete with known results.
- [ ] Runtime/readiness/smoke evidence exists when deployment is part of the claim.
- [ ] Rollback or recovery is understood for material side effects.

### Operations

- [ ] Logs/metrics/health state support the claimed runtime result.
- [ ] Scheduled work can recover, replay, or deduplicate as appropriate.
- [ ] Alerts/reports are actionable and avoid obvious noise.
- [ ] Privacy/security-sensitive telemetry has been scrubbed.

## Exceptions

For every skipped check that would normally be expected, record:

- what was skipped;
- why it was safe or necessary;
- what residual risk remains;
- what later evidence, if any, will close the gap.

## Completion rule

Do not convert `unknown`, `blocked`, `not run`, or `assumed` into `passed`. A smaller honest claim is better than a larger unsupported DONE claim.
