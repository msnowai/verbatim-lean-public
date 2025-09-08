**Goal tags:** [G1] Demo • [G2] Ops • [G3] FE • [G4] Analytics  
Roadmap: [[../03_Strategy/Roadmap.md]]

## Tickets (DoD inline)
- [ ] [G3] FE Compose → API (CORS ok) — Owner: Nowai — ETA: 2025-09-08 EOD PT  
    DoD: Next.js `/compose` POSTs to `${NEXT_PUBLIC_API_BASE}/api/comment`; renders `{verdict, cooldown_secs}`; **friendly error** shown for offline/4xx/5xx; API CORS allows `http://localhost:3000` and `http://127.0.0.1:3000`; **Evidence pasted** in Sprint.md: **Network 200 + JSON** receipt, browser console shows **no CORS** error, and screenshot/note of friendly error state; PR link included.

- [ ] [G2] CI path coverage — Owner: Nowai — ETA: 2025-09-08 EOD PT  
    DoD: Add `.github/workflows/ci.yml` with `on: pull_request` and `paths:` filters for `services/api-mock/**`, `frontend/**`, and `.github/workflows/ci.yml`; workflow runs on matching PRs; checks visible on PR page; link to workflow run + file path pasted in Sprint.md.

- [ ] [G4] EOD housekeeping — Owner: Nowai — ETA: 2025-09-08 5:00 PM PT  
    DoD: Post **SHIP_LOG** note; update **Mission_Control**; append stamp **“Docs fresh as of 2025-09-08 5:00 PM PT”**; move finished tickets to **Done** with date + PR link; reconcile carryovers (open → moved to tomorrow or closed); link to updated sections pasted in Sprint.md.