# Master Patch v51 — Three-Way Agent Bus (Lovable ⇄ GitHub ⇄ Cursor/Merlin)

Master: MARTECH. Audience: all main portals, sub-portals and slave portals. Supersedes v50 (still applies).

## 1. Agent contract in every repo (mandatory)
Every portal repo carries `.cursor/rules/martech-fleet.mdc` and `docs/AGENT-THREE-WAY-SYNC.md`.
Task briefs land in `.agent-tasks/queue/<task-id>--<slug>.md`; agents commit results to
`.agent-tasks/results/<task-id>.json` with `{ task_id, status, agent, summary, files_changed, commit }`.

## 2. Ingest + republish loop
The master ingests result files every 20 minutes (`/api/public/hooks/agent-bus`), records them on
`public.agent_tasks`, and calls `broadcastFleetRepublish` so every portal goes live with the change.
Push-based results may also POST to `/api/public/hooks/agent-task-result`.

## 3. Cursor background agents + access gate (new in v51)
When `CURSOR_API_KEY` exists, dispatch LAUNCHES a Cursor background agent instead of waiting for a
human pull. Before launching, the bus probes `GET /v0/repositories` and only launches on repos the
Cursor GitHub App can reach. If access is missing it records ONE actionable blocker
(`cursor_access_blocked`) instead of burning retries on a misleading "branch not found", and
auto-launches every pending brief on the first cycle after access is granted.

## 4. Self-healing
Stale dispatches are requeued with exponential backoff; failed launches are relaunched (bounded);
live agent status (RUNNING/FINISHED/ERROR + PR URL) is reconciled every cycle. Git-only handoff is
always the working floor — the bus never depends on the Cursor API being reachable.

## Required env
Master: `GITHUB_PATCH_TOKEN` (or workspace GitHub key), `AGENT_BUS_RUN_TOKEN`, optional
`CURSOR_API_KEY`, optional `MERLIN_API_KEY`. Slaves: nothing new.


<!-- applied-by: MARTECH master | version: v51 | reason: three-way agent bus + cursor access gate | at: 2026-08-12T19:12:52.501Z -->
