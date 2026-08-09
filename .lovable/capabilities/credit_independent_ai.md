# Capability: Credit-Independent AI & Next-Gen Media Engine
- **key**: `credit_independent_ai`
- **category**: ai
- **origin portal**: MARTECH
## What to implement
All AI chat/image/video/embeddings route through resilient wrappers supporting MiniMax video-01, Luma Reframe, Topaz Upscale, Google Imagen 4, Flux Pro/Dev, Ideogram v3 Turbo, CodeFormer, and GFPGAN; app runs with zero Lovable credits.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v3 | 2026-08-09T20:31:05.319Z -->
