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

## Decision outcomes

Every review should end in one of four states:

- **Promote** — move a repeated, beneficial practice into the shared baseline.
- **Keep** — evidence still supports the current rule.
- **Demote** — move a rule from default policy to optional reference/example.
- **Retire** — remove it because the underlying risk/control no longer justifies the cost.

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

## Suggested cadence

Do not review on a calendar merely to satisfy process. Review when evidence accumulates; for long-lived active ecosystems, a lightweight periodic sweep can still help detect stale rules.

The goal is not guideline completeness. The goal is a small, current baseline that improves delivery, safety, evidence quality, and resumability.
