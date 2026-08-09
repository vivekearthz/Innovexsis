# Capability: WhatsApp Mass Extraction & Round-Robin Broadcast
- **key**: `wa_bulk_rotation`
- **category**: whatsapp
- **origin portal**: MARTECH
## What to implement
Drive/contacts crawler, round-robin segment rotation, 100-140/day cap, approved-template sends, STOP/opt-out tracking, retry+fallback to plain text.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v2 | 2026-08-09T20:31:06.492Z -->
