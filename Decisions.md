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
- Demo UI polish scope — Keep demo UI minimal; run a ≤90-min “clarity pass” (copy, spacing, loading/state chips) with no new deps; verify FE→API still shows {verdict, cooldown_secs} — Rationale: hit Sprint’s functionality goals while removing avoidable rough edges that distract in the demo — Decided: 2025-08-26 — Revisit: 2025-09-03
# Target: docs/01_HQ/Decisions.md
- Demo focus (A/B/No-Go) — Prioritize fastest credible demo over polish; unblock G1 now and finish G3 wiring/verification, with design following minimally — Decided: 2025-08-28 — Revisit: 2025-09-04 PT

**A)** Stay the course: land **G1 Demo credibility** and **G3 FE Compose→API** now; keep design to microcopy + states needed for the demo path only.  
- Script + dry-run the demo flow (happy path + 1 recovery).  
- Verify FE→API path end-to-end (submit-time gate, cooldown, override).  
- Add minimal analytics stubs only to support the talk track (TTFP, pass rate).  
- Ship a one-pager demo brief (what, why, success).

**B)** Add a **2-week Design Clarity Sprint** (flows, empty/edge states, microcopy, and demo talk track), with **no new infra**; merge only text/UI clarity improvements.

**No-Go)** Change direction or expand scope (e.g., map UI, media uploads, profiles). This slips the demo and dilutes learning; defer until after the first credible run.

**Rationale**
- Credibility ≠ completeness; viewers need one crisp, working loop, not breadth.  
- G3 wiring is either merged or near-merge; finishing validation now de-risks the demo.  
- Design clarity helps, but two weeks up front delays hard evidence.  
- Minimal analytics stubs enable a data-anchored story without infra drag.  
- Keeping ≤3 tickets preserves velocity and reduces context switching.

**Risks & mitigations:**
- Demo looks bare → add microcopy, loading/empty states only where demo touches.  
- Hidden integration gaps → require a recorded smoke test of the full demo path before scheduling.  
- Missing metrics in the talk track → instrument just TTFP, pass rate, and override rate; screenshot dashboards.

**Recommendation:** **A** — Stay the course. It is the fastest path to a credible, testable demo while preserving focus; design polish can follow once the loop is proven.

- Choose Verb-First MVP over Globe-Map — Faster cold start - (verbs cluster globally), smaller scope (no map/geo), safer privacy surface; aligns with current Next.js + FastAPI slice and read-first, civility-gated posture — Decided: 2025-08-31 — Revisit: 2025-09-30
- 	•	English-only MVP (no geo UI) — Reduce complexity and moderation surface; aligns with early audience and demo goals — Decided: 2025-08-31 — Revisit: 2025-09-30
	•	Gate FP tolerance: ≤10% now → ≤5% by revisit — Accept some friction to uphold tone while we tune quiz and cooldowns — Decided: 2025-08-31 — Revisit: 2025-09-15
	•	Garmai leads Day-0 user seed — Fast path to credible first posts; equip with scripts + 10 starter verbs — Decided: 2025-08-31 — Revisit: 2025-09-07
	•	Demo success bar — WMC ≥50/week; Activation ≥70%; TTFP p50 ≤60s; Verified-pass ≥80%; Civility p90 ≥95%; Report rate ≤5/100 posts — Decided: 2025-08-31 — Revisit: 2025-09-30