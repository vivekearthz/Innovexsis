# Master Patch v55 — Permanent Lovable-Credit Freedom + Cursor Primary + 24h NVIDIA Model Discovery

Master: MARTECH. Audience: master portal, all sub-portals and all slave portals. Supersedes v51 (all earlier patches still apply).

## 1. The paid Lovable gateway is OFF by default (hard rule)
- `aiGatewayFetch` / `aiImageFetch` / `aiVideoFetch` / `embedTextsResilient` now gate every Lovable call behind `lovableAiEnabled()`, which requires `ALLOW_LOVABLE_AI=true` AND a key AND `SOVEREIGN_ONLY` unset.
- With no env vars at all a portal is permanently credit-free. Exhausted or removed Lovable credits can never break chat, image, vision, video or embeddings.
- Never `fetch("https://ai.gateway.lovable.dev/...")` directly and never throw on a missing `LOVABLE_API_KEY`.

## 2. Provider order (free-first, owned-second, paid-last)
1. NVIDIA NIM free ladders (live health registry)
2. Cursor (`CURSOR_API_KEY`, OpenAI-compatible) — the owner's already-paid primary environment
3. Merlin (`MERLIN_API_KEY`)
4. Sovereign non-US paid (DeepSeek → GLM → Qwen → Kimi)
5. Groq → OpenRouter → Pollinations keyless floor
6. Lovable gateway only if explicitly re-enabled

Degradation instead of failure: image/vision → text-only, video → image, embeddings → local deterministic 1536-dim vectoriser.

## 3. NVIDIA free-model discovery every 24 hours
The 02:30 IST orchestrator probes the live NVIDIA catalog, demotes 400/401/403/404/410/422 models instantly, re-promotes recovered ones, and AUTO-DISCOVERS catalog models missing from the static ladders (tagged `auto-discovered`, appended to the matching task ladder). Newly released free models are adopted within a day with no code change. 429/5xx/timeouts are transient and never demote.

## 4. Self-heal, retry and self-republish
Every stage retries with exponential backoff and bounded attempts. After the AI-independence stages pass, the orchestrator forces a fleet-wide republish and retries any portal that did not come back, so each portal re-publishes itself with the fix applied — no human intervention.

## Required environment
MASTER_HOST, MASTER_SYNC_SECRET, PRODUCT, REPUBLISH_HOOK_URL. Optional: NVIDIA_API_KEY_SECRET, CURSOR_API_KEY, MERLIN_API_KEY, GROQ_API_KEY, OPENROUTER_API_KEY. `LOVABLE_API_KEY` is NOT required anywhere.


<!-- applied-by: MARTECH master | version: v55 | reason: v55 credit-freedom + latest master codebase sync | at: 2026-08-13T19:19:16.458Z -->
