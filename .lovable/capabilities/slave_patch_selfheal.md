# Capability: Slave Patch Direct-Commit Self-Heal
- **key**: `slave_patch_selfheal`
- **category**: governance
- **origin portal**: MARTECH
## What to implement
Master commits MASTER_PATCH.md directly into each slave repo via GitHub Contents API, verifies presence (loopback), and re-applies drift on a cron.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v1 | 2026-08-09T20:30:59.386Z -->
