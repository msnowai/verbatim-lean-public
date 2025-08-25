**Goal tags:** [G1] Demo • [G2] Ops • [G3] FE • [G4] Analytics  
Roadmap: [[../03_Strategy/Roadmap.md]]

## Tickets (DoD inline)
- [ ] [G4] Instrument minimal events (stubs) — Owner: Dev Specialist (Interim Lead Dev) — ETA: 2025-08-26 EOD PT — DoD: Add INFO‑log stubs for `session_start`, `verb_click`, `post_drafted`, `post_submitted`, `gate_result`, `cooldown_started/ended`, `reflection_submitted` in FE/BE; no secrets; include 1–2 unit tests (shape only); paste receipts (log lines) under ticket.

    **Dev confirmation (paste receipts):**
    - BE Logs: Works confirmed by Nowai
    - FE logs: Not showing but confirmed and complete
    - Tests: paste tail from `pytest -q` (e.g., `2 passed`) for the new shape tests

- [ ] [G4] Dashboards scaffold — Owner: CoS — ETA: 2025-08-26 EOD PT — DoD: Create analytics note with formulas/queries for Activation, TTFP, Pass rate, Report rate, Cooldown recurrence, Cost/1k; link to “Analytics V0 — Events & Dashboards (G4)” in Roadmap; add screenshots/wireframes if any.


## Deferred
- (none; keeping ≤3 open)

## Carryovers (from yesterday) — Reconciled @ 2025-08-25 5:00 PM PT
> Rule: If PR merged → **Done** w/ date+link; else → request **self-test + ETA** and update ticket.
_No open carryovers; all items resolved or moved to Done._

## Done (carryovers closed today)
- [x] Merge PR: api-mock comment gate — **Done: 2025-08-23** — PR: https://github.com/msnowai/verbatim/pull/4
- [x] [G3] FE Compose → API (CORS ok) — **Done: 2025-08-24** — PR: https://github.com/msnowai/verbatim/pull/8
- [x] [G2] CI path coverage — **Done: 2025-08-24** — PR: https://github.com/msnowai/verbatim/pull/11
- [x] [G4] Analytics plan kickoff — **Done: 2025-08-25** — Link: docs/03_Strategy/Roadmap.md#analytics-v0--events--dashboards-g4
- [x] [G4] EOD housekeeping — **Done: 2025-08-25**

## PR Plan — G4: Instrument minimal events (stubs)

**Goal:** Add minimal, provider-agnostic event stubs (INFO logs only) across FE/BE so we can validate payload shapes before wiring PostHog.

### Files to touch (no secrets)
- **BE** `services/api-mock/`
  - Add INFO logs for:
    - `session_start`, `verb_click`, `post_drafted`, `post_submitted`,
      `gate_result`, `cooldown_started`/`cooldown_ended`, `reflection_submitted`
  - Tests: add 1–2 **pytest** “shape” tests (e.g., `gate_result` includes `{verb, verdict, cooldown_secs}`)
- **FE** `frontend/src/app/compose/page.tsx` (or equivalent)
  - Emit `post_drafted` (on textarea change) and `post_submitted` (on submit)
  - After response, `console.info("gate_result", { verdict, cooldown_secs })`

### Commands (dev)
```bash
# backend
cd services/api-mock
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
pytest -q   # expect: 2 passed (new shape tests)
python -m uvicorn app.main:app --reload --port 8000

# frontend (if present)
cd frontend
npm ci || npm install
[ -f .env.local ] || printf 'NEXT_PUBLIC_API_BASE=http://127.0.0.1:8000\n' > .env.local
npm run dev
```