# Master Patch v48 — Total Lovable Independence + Always-Answering Policy Endpoints

Master: MARTECH. Audience: all main portals, sub-portals and slave portals. Supersedes v47 (still applies).

## 1. Lovable-independent AI (mandatory)
- Every chat/image/video/embedding call MUST go through `aiGatewayFetch` / `aiImageFetch` / `aiVideoFetch` / `embedTextsResilient`.
- Provider order is FREE-FIRST: NVIDIA NIM → Groq → OpenRouter → Pollinations (keyless floor) → Lovable gateway only if a key happens to exist.
- A missing `LOVABLE_API_KEY` is never an error. No route may return `503 Gateway not configured`. No code may call the Lovable AI gateway directly.
- Degradation ladder instead of failure: image/vision → text-only, video → image, embeddings → local deterministic vectoriser.

## 2. Master AI gateway
`/api/public/ai-gateway` serves all slaves with zero credits. Auth stays `x-slave-key`; retry only 429/5xx responses and log every call.

## 3. Policy endpoints must never 500
`/api/public/portal/wa-policy`, `/api/public/portal/version`, and `/api/public/portal/instructions` are pure in-code projections with hardcoded fallback floors.

## 4. Repository durability and self-heal
The canonical master repository is `vivekearthz/my-secret-automagic-0ad5a80b` on `main`. Every verified portal repository mapping is pinned in code, the backend registry, and the private fleet registry. The daily 02:30 IST orchestrator restores mappings, retries Contents API writes, loopback-verifies this patch, and republishes the fleet. A transient 404, archive flag, duplicate heuristic, or workspace credential failure must never erase a pinned mapping.

## Required environment
MASTER_HOST, MASTER_SYNC_SECRET, PRODUCT, REPUBLISH_HOOK_URL. Optional: NVIDIA_API_KEY_SECRET, GROQ_API_KEY, OPENROUTER_API_KEY.


<!-- applied-by: MARTECH master | version: v48 | reason: loopback-self-heal | at: 2026-08-07T08:12:23.019Z -->
