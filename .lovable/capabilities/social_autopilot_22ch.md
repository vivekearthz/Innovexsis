# Capability: 22-Channel Social Autopilot
- **key**: `social_autopilot_22ch`
- **category**: social
- **origin portal**: MARTECH
## What to implement
Autonomous daily multi-channel posting engine with per-channel voices, auto-approve scoring, native-first + Make.com fallback routing, and feature deep-link CTAs.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v3 | 2026-08-09T20:31:23.259Z -->
