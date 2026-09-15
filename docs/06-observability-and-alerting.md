# Observability and Alerting

## Observe the outcome, not only the process

Instrumentation should help answer whether the system is delivering the intended outcome, where it is failing, and whether intervention is required.

Use the signal source closest to the failure mode:

- application exceptions and release regressions → error monitoring;
- latency, saturation, queue depth, host/runtime health → metrics/log monitoring;
- cloud resource health → provider-native monitoring;
- critical user journeys → synthetic/browser/API checks;
- cost, quota, stale resources, drift, backup age, certificate expiry and cross-system conditions → scheduled deterministic scans.

The exact vendor is project-specific.

## Alert versus report

An **alert** should imply timely action. A **report** communicates state or trend without requiring immediate interruption.

Do not turn every metric change into an alert. Prefer scheduled summaries for conditions that are useful to review but not urgent.

## Deterministic detection first

When a condition can be defined from facts or metrics, prefer:

`deterministic collector/detector -> optional AI interpretation -> notification/action`

AI can summarize, explain, group, prioritize, or propose next actions. It should not be the sole detector for a condition that can be checked reliably in code.

## Useful alert content

An actionable alert should contain enough context to decide what to do next:

- severity;
- system/environment;
- condition and observed value;
- threshold/baseline when relevant;
- detection time and current status;
- likely impact;
- link to dashboard/log/report/evidence;
- runbook or next action when one exists;
- release/change context when useful.

Avoid dumping raw logs or sensitive payloads into notification channels.

## Noise control

Use techniques appropriate to the signal:

- sustained-window or M-of-N evaluation;
- baseline/anomaly comparison;
- cooldown and deduplication;
- warning versus critical thresholds;
- aggregation of repeated events;
- explicit recovery notification where it helps close the loop.

Repeated noisy alerts are a reliability defect because they train the operator to ignore the channel.

## Monitor the monitoring

For important alert paths, periodically prove the full path works:

`safe trigger/test signal -> detector -> notification delivery -> usable context`

A configured alert that never receives data or whose notification path is broken is not working monitoring.

## Privacy and secrets

Treat webhook URLs, credentials, auth headers, cookies, tokens, personal identifiers and sensitive payloads as secrets/private data. Scrub them before telemetry leaves the application boundary.

Observability is not permission to collect everything. Capture the minimum data needed to diagnose and operate the system.

## Maturity guidance

- **Prototype/PoC** — logs and manual inspection may be enough.
- **MVP** — capture material failures and basic runtime health.
- **Pilot/Beta** — add actionable alerts for critical paths, readiness/health, and meaningful cost/usage conditions.
- **Production/long-lived** — add ownership, noise control, alert-path verification, trend reporting, and recovery evidence for important systems.
