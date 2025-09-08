## Project Snapshot (Read First, Ground All Advice In This)
Last updated: 2025-08-24

### Goals (this 30 days)
- **G1 Demo credibility**  • **G2 Agent Ops**  • **G3 FE Compose→API**  • **G4 Analytics (stub)**

See [[./Roadmap.md]] for outcomes/KPIs and ticket mapping.
### Current State (≤200 words)
- **Features:** FastAPI mock with `/health` and `/api/comment` (tone gate + cooldown with in‑memory persistence); structured `gate_result` logging; mirror workflow keeps the 4 Lean docs fresh; minimal FE **/compose** page (Next.js) posts to the mock and renders `{verdict, cooldown_secs}`; Daily Ops Playbook + ≤3‑ticket rule; Carryovers reconciliation at EOD. **PRs:** #4 merged (api‑mock demo path); #8 open (FE Compose → API); CI path‑coverage PR planned.
- **Assumptions:** Demo‑first is the fastest path to credibility; aura/tone are **private** (no public scores); cooldowns are **calm, not punitive**; agents produce **one paste‑to‑file block per reply**; keep ≤3 open tickets, move extras to **Deferred (tomorrow)**.
- **Target user (now):** English‑speaking early adopters (college creatives/writers, Reddit/Twitter migrants) seeking a lower‑tox, read‑first space in US/Canada.

### Stack & Architecture
- **Clients:** Web (Next.js App Router) — minimal **/compose** demo; **Mobile:** not started.  **Backend:** Python **FastAPI** mock; **DB:** none (in‑memory cooldowns). 
- **Auth/moderation:** Not integrated; tone rules are rules‑based (keywords); appeals/reporting deferred.
- **Analytics/experimentation:** Server log line per request (`gate_result …`); PostHog keys **stubbed** in `.env.example`; no flags/experiments yet.
- **Notable constraints:** Solo+AI team; mirror publishes only the 4 Lean docs; local CORS only (`http://localhost:3000` / `http://127.0.0.1:3000`); time‑boxed to a credible 3‑min demo before broader build‑out.