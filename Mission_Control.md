# Mission Control
**Sprint goals:** G1 Demo • G2 Ops • G3 FE • G4 Analytics
**Date:** 2025-08-28
> [!info]+ CoS Dashboard (standing)
> **Daily SLAs**
> - [ ] Morning handoff posted by **9:00 AM PT**
> - [ ] EOD rollup posted by **5:00 PM PT**
> - [ ] ≤3 tickets today (Owner / ETA / DoD)
> - [ ] Append freshness stamp at end of EOD: _Docs fresh as of YYYY-MM-DD h:mm AM/PM PT._
>
> **Escalate only if**
> - Blocker ≥4h on a critical ticket
> - Interviews <2 by Day 3 or <5 by Day 6; Pre-signups <10 by Day 10
> - Demo flow broken / mirror not updating
>
> **Links**
> - [[../04_Sprint/Sprint.md]] • [[./Decisions.md]] • [[../03_Strategy/Project_Snapshot.md]]

## Morning handoff (CoS @ 9am PT)
_Stamped: 2025-08-28 9:00 AM PT_

### Today’s Top 3
1) **[G4] KPI counters (Activation / TTFP — initial)**  
   DoD: using current stubs/logs (or gated events), produce first counts for **Activation** and **TTFP (p50/p90)**; add formulas + “source” notes and a small calc table to `docs/03_Strategy/Analytics_Dashboards.md`; paste screenshot + brief method in Sprint.

2) **[G4] Design Clarity — Flows & Demo Talk Track (no new infra)**  
   DoD: map the end-to-end **flow diagram** (Home → Verb → Compose → Tone → Cooldown → Reflection → Post → History); list **UI states** per step; draft a **90‑sec demo talk track**; paste into `docs/References/microcopy.md` and link from `Demo_Checklist.md`.

3) **EOD housekeeping**  
   DoD: add SHIP_LOG note; Links/Targets reflect merged PRs; post EOD by 5pm PT; append freshness stamp.

### Blockers
- **None active** — All prior blockers cleared. We’re soft-enforcing merges on a private Free repo: merge only when CI is **green** and Sprint receipts are pasted. Revisit hard enforcement if repo goes public or moves to Team.
### Links/Targets
- Sprint (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Sprint.md
- Decisions (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Decisions.md
- Mission_Control (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Mission_Control.md
- Project_Snapshot (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Project_Snapshot.md
- Dashboards note (G4): docs/03_Strategy/Analytics_Dashboards.md
- PR #4: https://github.com/msnowai/verbatim/pull/4 — **Merged**
- PR #8: https://github.com/msnowai/verbatim/pull/8 — **Merged**
- Compare (api-mock): https://github.com/msnowai/verbatim/compare/main...feat/api-mock-comment-gate
- Compare (git-cleanup): https://github.com/msnowai/verbatim/compare/main...chore/git-cleanup
- PR #11 (CI path coverage): https://github.com/msnowai/verbatim/pull/11 — **Merged**
- PR #14 (docs — Sprint carryovers): https://github.com/msnowai/verbatim/pull/14 — **Merged**
- PR #21 (CI verify): https://github.com/msnowai/verbatim/pull/21 — **Merged**
- PR #32: https://github.com/msnowai/verbatim/pull/32 — **Merged**
- PR #27 (G4 PostHog wiring): https://github.com/msnowai/verbatim/pull/27 — **Merged**
- PR #28 (dashboards screenshots): https://github.com/msnowai/verbatim/pull/28 — **Merged**
- PR #29 (weekly snapshot template + script): https://github.com/msnowai/verbatim/pull/29 — **Merged**
- PR #33 (api-mock analytics + tests): https://github.com/msnowai/verbatim/pull/33 — **Merged**
- PR #35: https://github.com/msnowai/verbatim/pull/35 — **Merged**
- PR #36 (G4 PostHog wiring): https://github.com/msnowai/verbatim/pull/36 — **Merged**
- PR #37 (G4 PostHog wiring): https://github.com/msnowai/verbatim/pull/37 — **Merged**
- PR #38: https://github.com/msnowai/verbatim/pull/38 — **Open**

## 2025-08-25
- Shipped: Roadmap **Analytics V0** section added; Sprint kept at ≤3 with G4 focus.
- PRs: #8 **merged** (FE Compose → API), #11 **merged** (CI path coverage), #14 **merged** (docs — carryovers)
- Tests: api-mock local green — ruff + black + pytest (4 passed)
- Next: begin G4 instrumentation stubs (logs only) and dashboards scaffold; paste receipts in Sprint

## EOD rollup (CoS @ 5pm PT)
_Docs fresh as of 2025-08-28 5:00 PM PT._

### Shipped
- **[G4] PostHog wiring (config-gated)** — merged to main (commit linked in Sprint Done).
- **[G4] KPIs query stubs & screenshots** — **PR #28 merged**; dashboards note updated with real screenshots + capture guide.
- **Docs ops** — Weekly Snapshot template + script **PR #29 merged**; Morning handoff update **PR #32 merged**.
- **Sprint hygiene** — Kept ≤3 open; moved merged items to **Done** with date + link; carryovers reconciled.

### Tests & PR
- **Local checks:** backend ruff + black + pytest — green.
- **PRs/commits today:**  
  - #27 (PostHog wiring config-gated) — **Merged** (commit in Sprint Done)  
  - #28 (dashboards screenshots) — **Merged**  
  - #29 (weekly snapshot template + script) — **Merged**  
  - #32 (MC morning handoff) — **Merged**

### Links
- PR #4: https://github.com/msnowai/verbatim/pull/4 — **Merged**
- PR #8: https://github.com/msnowai/verbatim/pull/8 — **Merged**
- PR #11: https://github.com/msnowai/verbatim/pull/11 — **Merged**
- PR #14: https://github.com/msnowai/verbatim/pull/14 — **Merged**
- PR #33 (api-mock analytics + tests): https://github.com/msnowai/verbatim/pull/33 — **Merged**
- PR #27 (G4 PostHog wiring): https://github.com/msnowai/verbatim/pull/27 — **Merged**
- PR #28 (dashboards screenshots): https://github.com/msnowai/verbatim/pull/28 — **Merged**
- PR #29 (weekly snapshot): https://github.com/msnowai/verbatim/pull/29 — **Merged**
- PR #32 (MC morning handoff): https://github.com/msnowai/verbatim/pull/32 — **Merged**

### Risks
- **Soft enforcement** (private Free repo): required checks aren’t enforced by GitHub on private Free. Continue to gate merges on **CI green + Sprint receipts**. Revisit hard enforcement if repo goes public or moves to Team.

## Blocker Playbook (standing)
1) Set Owner + Unblock-by (today or tomorrow).
2) Make a 1-ticket fix in Sprint (Owner/ETA/DoD).
3) Run quick commands (below); paste evidence (EOD).
4) If still blocked → escalate in Morning handoff.

### Quick commands
<details>
<summary><strong>Dev quick commands (collapsed)</strong></summary>

```bash
# Free ports (API 8000, FE 3000)
lsof -ti :8000 | xargs -r kill -9 || true
lsof -ti :3000 | xargs -r kill -9 || true

# Backend: run api-mock
cd services/api-mock
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m uvicorn app.main:app --reload --port 8000

# Frontend (if present)
cd frontend
npm ci || npm install
[ -f .env.local ] || printf 'NEXT_PUBLIC_API_BASE=http://127.0.0.1:8000\n' > .env.local
npm run dev

# CI workflow presence
[ -f .github/workflows/ci.yml ] && echo "ci.yml ok" || echo "ci.yml MISSING"
```

</details>

<!-- REQUIRE_FRESHNESS_STAMP: append "_Docs fresh as of YYYY-MM-DD h:mm AM/PM PT._" at the end of EOD whenever this file is updated. -->
