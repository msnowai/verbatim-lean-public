# Mission Control
**Sprint goals:** G1 Demo • G2 Ops • G3 FE • G4 Analytics
**Date:** 2025-08-25
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

_Stamped: 2025-08-25 9:00 AM PT_
## Today’s Top 3 
1) **FE Compose → API (CORS ok) — PR #8 merged** — DoD: update Sprint to move the ticket to **Done (date + link)**; ensure Dev receipts are pasted under the Sprint ticket; update Links/Targets status.
2) **CI path coverage — PR #11 merged** — DoD: move CI ticket to **Done (date + link)** in Sprint; confirm CI jobs run on new PRs; maintain soft-enforce policy (merge only when CI is green).
3) **EOD housekeeping** — DoD: add SHIP_LOG note; update Links/Targets to reflect merged PRs; post EOD rollup by 5pm PT; append freshness stamp at end of EOD.

### Links/Targets
- Sprint (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Sprint.md
- Decisions (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Decisions.md
- Mission_Control (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Mission_Control.md
- Project_Snapshot (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Project_Snapshot.md
- PR #4: https://github.com/msnowai/verbatim/pull/4
- PR #8: https://github.com/msnowai/verbatim/pull/8
- Compare (api-mock): https://github.com/msnowai/verbatim/compare/main...feat/api-mock-comment-gate
- Compare (git-cleanup): https://github.com/msnowai/verbatim/compare/main...chore/git-cleanup
- PR #11 (CI path coverage): https://github.com/msnowai/verbatim/pull/11
- PR #14 (docs — Sprint carryovers): https://github.com/msnowai/verbatim/pull/14 — **Merged**

## 2025-08-25
- Shipped: Roadmap **Analytics V0** section added; Sprint kept at ≤3 with G4 focus.
- PRs: #8 **merged** (FE Compose → API), #11 **merged** (CI path coverage), #14 **merged** (docs — carryovers)
- Tests: api-mock local green — ruff + black + pytest (4 passed)
- Next: begin G4 instrumentation stubs (logs only) and dashboards scaffold; paste receipts in Sprint

## EOD rollup (CoS @ 5pm PT)
### Shipped
- **FE Compose → API** — **PR #8 merged**; `/compose` posts to `${NEXT_PUBLIC_API_BASE}/api/comment` and renders `{verdict,cooldown_secs}` with friendly error state; receipts posted in Sprint.
- **CI path coverage** — **PR #11 merged**; `.github/workflows/ci.yml` added with `paths:` for `services/api-mock/**` and `frontend/**`; jobs run on PRs (api_mock + frontend).
- **Sprint hygiene** — Tickets kept at **≤3**; merged items moved to **Done** with date + link; carryovers reconciled.

### Tests & PR
- **Local checks:** ruff + black + pytest (**4 passed**) on api-mock.
- **PRs:** #4 **merged** (api-mock demo UI + gate) • #8 **merged** (FE Compose → API) • #11 **merged** (CI path coverage)

### Links
- PR #4: https://github.com/msnowai/verbatim/pull/4 — **Merged**
- PR #8: https://github.com/msnowai/verbatim/pull/8 — **Merged**
- PR #11: https://github.com/msnowai/verbatim/pull/11 — **Merged**

### Risks
- **Soft enforcement** (private Free repo): branch protection required checks aren’t enforced by GitHub. Mitigation: use CI status + PR checklist; merge only when green. Revisit if repo goes public or moves to Team plan.
- **Next work** (tomorrow): monitor CI on a fresh PR to confirm path filters; keep Sprint ≤3; add any missing receipts/screenshots to Sprint tickets.

_Docs fresh as of 2025-08-24 5:00 PM PT._

## Blocker Playbook (standing)
1) Set Owner + Unblock-by (today or tomorrow).
2) Make a 1-ticket fix in Sprint (Owner/ETA/DoD).
3) Run quick commands (below); paste evidence (EOD).
4) If still blocked → escalate in Morning handoff.

### Quick commands
# Branch protection (process only; GUI step)
# GitHub → Repo → Settings → Branches → “Add rule” for main:
# - Require a pull request before merging
# (Optionally add CI checks later.)

# Git hygiene (safe cleanup)
git rm -r --cached --ignore-unmatch .venv node_modules dist build coverage || true
git ls-files -z | xargs -0 -I{} bash -lc '[[ "{}" == *"__pycache__"* || "{}" == *".pytest_cache"* ]] && git rm -rf --cached "{}" || true'
git add .gitignore && git commit -m "chore: ignore env/node/build artifacts" || true
# (Optional, removes ignored files from disk)
git clean -n -Xdf   # preview
git clean -Xdf      # apply

# Port already in use (API 8000, FE 3000)
lsof -ti :8000 | xargs -r kill -9 || true
lsof -ti :3000 | xargs -r kill -9 || true
# Or run on alternate port:
# uvicorn app.main:app --reload --port 8001
# npm run dev -- -p 3001

# FE base URL (env)
printf 'NEXT_PUBLIC_API_BASE=http://127.0.0.1:8000\n' > frontend/.env.local

<!-- REQUIRE_FRESHNESS_STAMP: append "_Docs fresh as of YYYY-MM-DD h:mm AM/PM PT._" at the end of EOD whenever this file is updated. -->
