# Decisions (append-only)
- CoS scope & SLA — CoS owns daily ops (Morning handoff by 9am PT, EOD rollup by 5pm PT), ticketizer (≤3 tickets/day), Specialist Slot orchestration (Dev/Designer/QA), mirror health checks; escalate only on blockers ≥4h, interview/demo target risk, or mirror outage — Decided: 2025-08-21 — Revisit: 2025-09-15
- CoS scope & SLA — CoS owns daily ops (Morning handoff by 9am PT, EOD rollup by 5pm PT), ticketizer (≤3 tickets/day), Specialist Slot orchestration (Dev/Designer/QA), mirror health checks; escalate only on blockers ≥4h, interview/demo target risk, or mirror outage — Rationale: lock daily cadence for Sprint 01, free founder for approvals/interviews, and set clear escalation gates to protect demo readiness — Decided: 2025-08-23 — Revisit: 2025-09-15
## Branch protection enforcement (private Free repo)
- Decision: Use **soft enforcement** (CI + Auto-merge + receipts) until we (a) make the repo public or (b) move to an Org with GitHub Team.
- Rationale: Keep velocity now; cost/visibility later.
- Operating Rules:
  - Only merge via **Auto-merge** when all CI jobs are green.
  - Paste Dev receipts under Sprint ticket before enabling Auto-merge.
  - No manual “Merge” button presses.
- Revisit: in 2 weeks or when 2+ collaborators join.
## Branch protection enforcement (private Free repo)
- Decision: Use **soft enforcement** (CI status + PR checklist) until we (a) make repo public or (b) move to a Team org.
- Rules of engagement:
  - Do not click “Merge” unless CI is green and receipts are pasted in Sprint.
  - Keep ≤3 open tickets; move finished to Done with date + PR link.
- Revisit: in 2 weeks or when we add another collaborator.