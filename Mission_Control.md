
## Morning handoff (CoS @ 9am PT)

Top 3 (Nowai):
1) [G3] FE Compose → API (CORS ok) — finalize open PR; add **friendly error** for offline/4xx/5xx; paste receipts (**Network 200 + JSON**, no CORS errors on /compose).
2) [G2] CI path coverage — add `.github/workflows/ci.yml` with `paths:` for `services/api-mock/**`, `frontend/**`, and the workflow itself; confirm checks appear on matching PRs.
3) [G4] EOD housekeeping — post **SHIP_LOG** note; update Mission_Control; append **“Docs fresh as of … PT”** stamp; reconcile any carryovers.

Blockers:
- None active (mirrors reachable; soft-enforcement continues until repo/public or Team plan).

Links/Targets:
- Sprint (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Sprint.md
- Decisions (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Decisions.md
- Mission_Control (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Mission_Control.md
- Project_Snapshot (mirror): https://raw.githubusercontent.com/msnowai/verbatim-lean-public/main/Project_Snapshot.md
- Today’s touch points: `frontend/app/compose/page.tsx` • `frontend/lib/api.ts` • `services/api-mock/app/main.py` • `.github/workflows/ci.yml`