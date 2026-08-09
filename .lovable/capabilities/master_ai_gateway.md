# Capability: Master AI Gateway Proxy
- **key**: `master_ai_gateway`
- **category**: ai
- **origin portal**: MARTECH
## What to implement
Central OpenAI-compatible AI gateway slaves call with x-slave-key so they hold no AI credentials; maps model names to backing providers including latest image/video generation and restoration models.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v2 | 2026-08-09T20:31:02.889Z -->
