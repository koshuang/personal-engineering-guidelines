# Guideline Evolution

These guidelines are an evidence-driven baseline, not a one-way accumulation of rules.

## Review triggers

Review a guideline when one or more of these occur:

- the same failure or workaround appears in multiple projects;
- a project repeatedly ignores a rule because it blocks delivery without reducing meaningful risk;
- a tool or platform change makes the original control obsolete;
- a rule duplicates a stronger mechanical control in tests, CI, runtime, or infrastructure;
- operating cost, CI cost, maintenance burden, or agent-context cost becomes material;
- a production incident, recovery, privacy, security, or continuity problem exposes a missing capability;
- a project advances from Prototype/PoC into Pilot/Production.

A review is **signal-triggered, not schedule-triggered**. An automation run, elapsed time, or lack of recent edits is not by itself a reason to review or change the guideline.

## Decision outcomes

Every review should end in one of four states:

- **Promote** — move a repeated, beneficial practice into the shared baseline.
- **Keep** — evidence still supports the current rule.
- **Demote** — move a rule from default policy to optional reference/example.
- **Retire** — remove it because the underlying risk/control no longer justifies the cost.

A valid outcome is also **no change** when the observed evidence is isolated, ambiguous, or already handled by project-local rules.

## Promotion test

Before promoting a rule, ask:

1. What outcome or recurring failure does it improve?
2. Is the pattern repeated, strategically intentional, or high-consequence enough to generalize?
3. Can the same outcome be achieved with a cheaper or more mechanical control?
4. Does the rule describe a capability rather than overfitting to one vendor or framework?
5. What evidence would later justify demotion or retirement?

## Demotion test

A guideline is a demotion candidate when it repeatedly:

- delays trustworthy feedback without materially reducing risk;
- duplicates tests, CI, runtime guards, or platform controls;
- creates artifacts nobody uses for decisions or recovery;
- raises cognitive/context cost more than it improves continuity;
- becomes compliance theater;
- overfits one project, technology, or historical incident.

Safety/privacy controls are not demoted merely because they are inconvenient. The underlying risk must be removed, replaced by a stronger control, or explicitly accepted.

## Evidence discipline

Public guidance contains the reusable principle. Private evidence may preserve repository names, contribution attribution, failure details, measurements, and promotion/demotion rationale.

When a rule changes, preserve enough decision history to answer:

- Why did this rule exist?
- What evidence changed?
- What replaced it, if anything?

Prefer the closest objective evidence available: current-head CI/job/step, runtime readback, production/recovery evidence, or a repeated cross-project decision pattern. Avoid changing shared guidance from an aggregate status, one anecdote, or speculative trend alone.

## Review routing

Project delivery remains the default priority. Surface guideline-review work only when execution produces a meaningful signal, such as:

- maturity or risk materially changed;
- the same local override recurs across projects;
- a shared rule repeatedly causes delivery friction without reducing risk;
- a mechanical control has replaced a prose rule;
- project-profile or canonical-source routing materially helps or misleads decisions.

Capture the private evidence first, then decide Promote / Keep / Demote / Retire. Do not create backlog merely to maintain the guideline.

## Cadence

Do not review on a calendar merely to satisfy process. Review when evidence accumulates. A lightweight sweep is only useful when it is looking for concrete drift or accumulated signals; an empty sweep should remain a no-op.

The goal is not guideline completeness. The goal is a small, current baseline that improves delivery, safety, evidence quality, and resumability.
