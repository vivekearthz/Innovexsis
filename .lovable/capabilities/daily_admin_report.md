# Capability: Daily Admin Report + Web Push
- **key**: `daily_admin_report`
- **category**: reporting
- **origin portal**: MARTECH
## What to implement
12:05 AM IST report of all posts/WhatsApp/email sent, emailed to the owner, with CXO recharts dashboard and VAPID web-push alerts.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v1 | 2026-08-09T20:31:11.207Z -->
