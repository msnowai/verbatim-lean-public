**Goal tags:** [G1] Demo • [G2] Ops • [G3] FE • [G4] Analytics  
Roadmap: [[../03_Strategy/Roadmap.md]]

## Tickets (DoD inline)
- [ ] [G4] Microcopy & States Polish (UI text only) — Owner: Designer — ETA: 2025-09-05 EOD PT — DoD: update **labels, helpers, toasts** (aligned/borderline/triggering/cooldown + error cases) in `docs/References/microcopy.md`; add **before/after screenshots** to `docs/03_Strategy/assets/` and embed in `Analytics_Dashboards.md` “Screenshots (evidence)”; link changes in Sprint.

## Clarity Sprint (2025-08-28 → 2025-09-11) — Plan (docs-first, no infra)
- **Week 1:** Flows & talk track → Microcopy pass → collect screenshots
- **Week 2:** Demo UX nits (tiny only) → rehearse script → finalize evidence

## Deferred
- (none; keeping ≤3 open)

## Carryovers (from yesterday) — Reconciled @ 2025-08-31 9:00 AM PT

> Rule: If PR merged → **Done** w/ date+link; else → request **self-test + ETA** and update ticket.
_No open carryovers; all items resolved or moved to Done._

## Done (carryovers closed today)
- [x] Merge PR: api-mock comment gate — **Done: 2025-08-23** — PR: https://github.com/msnowai/verbatim/pull/4
- [x] [G3] FE Compose → API (CORS ok) — **Done: 2025-08-24** — PR: https://github.com/msnowai/verbatim/pull/8
- [x] [G2] CI path coverage — **Done: 2025-08-24** — PR: https://github.com/msnowai/verbatim/pull/11
- [x] [G4] Analytics plan kickoff — **Done: 2025-08-25** — Link: docs/03_Strategy/Roadmap.md#analytics-v0--events--dashboards-g4
- [x] [G4] EOD housekeeping — **Done: 2025-08-25**
- [x] BE: analytics stub + typing + test fix — **Done: 2025-08-28** — PR: https://github.com/msnowai/verbatim/pull/33
- [x] [G4] Instrument minimal events (stubs) — **Done: 2025-08-26** — PR: <link>
- [x] [G4] Dashboards scaffold — **Done: 2025-08-26** — PR: https://github.com/msnowai/verbatim/pull/20
- [x] [G4] KPIs query stubs & screenshots — **Done: 2025-08-27** — PR: https://github.com/msnowai/verbatim/pull/28
- [x] Docs: Weekly Project Snapshot template + script — **Done: 2025-08-28** — PR: https://github.com/msnowai/verbatim/pull/29
- [x] [G4] PostHog wiring (config-gated) — **Done: 2025-08-28** — PR: https://github.com/msnowai/verbatim/pull/36
- [x] [G4] KPI counters (Activation / TTFP — initial) — **Done: 2025-08-31** — Link: docs/03_Strategy/Analytics_Dashboards.md
- [x] [G4] Design Clarity — Flows & Demo Talk Track — **Done: 2025-08-31** — Link: docs/References/microcopy.md#g4-talk-track, - Evidence: Activation 2/3 (66.7%), TTFP p50=73s p90=105s (staging counters 2025-08-31)
  - Table pasted into Analytics_Dashboards (Activation/TTFP)

### Commands (staging demo → then branch/PR)
```bash
# 1) Run the counters on the sample (staging)
python agents/runs/2025-08-28/code/metrics/kpi_counters.py \
  --input agents/runs/2025-08-28/code/metrics/activation_sample.csv

# 2) Paste the printed summary + small table into Analytics_Dashboards.md (Activation & TTFP),
#    under "Dashboards & targets": add a "Source: staging counters (YYYY-MM-DD)" line.

# 3) Branch & PR (docs-only)
BR="docs/g4-kpi-counters-$(date +%Y%m%d-%H%M)"
git switch -c "$BR" || git switch "$BR"
git add docs/03_Strategy/Analytics_Dashboards.md agents/runs/2025-08-28/code/metrics/*
git commit -m "docs(g4): initial Activation/TTFP counters (staging) + calc table and method notes"
git push -u origin "$BR"
# gh pr create -B main -H "$BR" -t "docs(g4): Activation/TTFP counters (staging)" -b "Adds first counts and method table" 
