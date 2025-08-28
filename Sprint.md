**Goal tags:** [G1] Demo • [G2] Ops • [G3] FE • [G4] Analytics  
Roadmap: [[../03_Strategy/Roadmap.md]]

## Tickets (DoD inline)

- [ ] [G4] PostHog wiring (config-gated) — Owner: Dev Specialist (Interim Lead Dev) — ETA: 2025-08-28 EOD PT — DoD: Add config-gated PostHog stubs on BE/FE; `.env.example` placeholders only (no secrets); one toggled test event behind a flag; update `Analytics_Dashboards.md` “source” notes; paste receipts (logs + config snippet) under ticket. — **PR #27:** https://github.com/msnowai/verbatim/pull/27
- [ ] [G4] KPI counters (Activation / TTFP — initial) — Owner: Dev Specialist + CoS — ETA: 2025-08-29 EOD PT — DoD: Using current stubs/logs (or gated events), produce first counts for **Activation** and **TTFP (p50/p90)**; add formulas + “source” notes and a small calc table to `Analytics_Dashboards.md`; paste screenshot + brief method in Sprint.

## Deferred
- (none; keeping ≤3 open)

## Carryovers (from yesterday) — Reconciled @ 2025-08-26 9:00 AM PT

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

- [x] [G4] KPIs query stubs & screenshots — **Done: 2025-08-27** — PR: https://github.com/msnowai/verbatim/pull/28

Paste into: docs/04_Sprint/Sprint.md
Action: APPEND

## PR Plan — [G4] PostHog wiring (config-gated)

**Goal:** Add **config-gated** analytics stubs so we can flip on PostHog later without secrets or network calls today. BE logs route through a tiny helper; FE emits a safe stub if a flag is set. Keep to **≤3 files**.

### Files to change/add (≤3 total)
1) **ADD** `services/api-mock/analytics.py` — helper with `track(event, props)`; respects `POSTHOG_ENABLED` env; logs only (no network, no secrets).
2) **EDIT** `services/api-mock/app/main.py` — import `track` and mirror key events behind the helper (`session_start`, `post_submitted`, `gate_result`, `cooldown_*`).
3) **EDIT** `frontend/src/app/compose/page.tsx` — optional FE stub: if `process.env.NEXT_PUBLIC_PH_ENABLED === 'true'`, emit `window.posthog?.capture('gate_result', {…})`. (No new deps, no keys; safe if PostHog JS isn’t present.)

> Notes  
> • Back-end placeholders live in **existing** `services/api-mock/.env.example` (already tracked) — add `POSTHOG_ENABLED=false`, `POSTHOG_HOST`, `POSTHOG_PROJECT_API_KEY` placeholders in that file after this PR (or include in a follow-up docs PR if you prefer to keep the 3-file cap).  
> • FE flag reads `NEXT_PUBLIC_PH_ENABLED`. Don’t ship keys; set via local `.env.local` when you’re ready.

### Commands (dev → branch → PR)
```bash
BR="feat/g4-posthog-stubs-$(date +%Y%m%d-%H%M)"
git switch -c "$BR" || git switch "$BR"

# (re)create backend venv and run tests
cd services/api-mock
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
pytest -q
deactivate
cd - >/dev/null

# (optional) FE quick smoke
if [ -d frontend ]; then
  cd frontend
  npm install
  # npm run dev   # manual check prints local URL; stop after it boots
  cd - >/dev/null
fi

git add -A
git commit -m "feat(g4): config-gated analytics stubs (BE helper + FE capture stub); no secrets"
git push -u origin "$BR"

# open PR (CLI or browser)
gh pr create -B main -H "$BR" \
  -t "feat(g4): config-gated analytics stubs (BE helper + FE capture stub)" \
  -b "Adds BE analytics helper (logs only) + FE capture stub under env flags. No secrets; no new deps. Future PR can swap to real PostHog."
# browser fallback:
# open "https://github.com/<org>/<repo>/compare/main...$BR"



Paste into: docs/04_Sprint/Sprint.md
Action: APPEND

## PR Plan — [G4] KPIs query stubs & screenshots

**Goal:** Ship a clear, reviewable dashboards note with **real, readable screenshots** (not placeholders) and query stubs for the alpha KPIs. Everything stays in docs; no code/services touched.

### Files to change / add
1) **UPDATE** `docs/03_Strategy/Analytics_Dashboards.md` — append a **“Screenshots (evidence) + Capture guide”** section (block below).
2) **ADD** `docs/03_Strategy/assets/` — put **your actual PNGs** here with fixed names:
   - `dashboards_wireframe.png` — a wireframe/screenshot of the KPI card layout
   - `activation_calc_table.png` — a screenshot of a tiny calc table you create (see guide)
3) *(Optional)* **ADD** `docs/03_Strategy/assets/activation_sample.csv` — the 3–5 row input you use to generate the calc table screenshot (helps reviewers reproduce).

### Content to append in `docs/03_Strategy/Analytics_Dashboards.md`
```md
## Screenshots (evidence)

- Dashboards wireframe  
  ![Dashboards wireframe](assets/dashboards_wireframe.png)

- Activation calc table  
  ![Activation calc table](assets/activation_calc_table.png)

### Capture guide (so reviewers can reproduce)
1) **Wireframe:** In your notes or a design tool (Figma/Excalidraw/Obsidian canvas), lay out cards for: Activation, TTFP (p50/p90), Verified pass rate, Report rate, Cooldown recurrence, Cost/1k. Take a clean PNG screenshot and save as `assets/dashboards_wireframe.png`.
2) **Activation sample:** Create a tiny table (3–5 users: session_start, first post, delta s, counted). Take a screenshot and save as `assets/activation_calc_table.png`.  
   *(Optional)* Save the inputs as `assets/activation_sample.csv` for reviewers.

> Evidence is **docs-only** and must render in GitHub/Obsidian preview with these exact filenames.