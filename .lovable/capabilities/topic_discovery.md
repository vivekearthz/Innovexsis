# Capability: AI Topic Discovery
- **key**: `topic_discovery`
- **category**: content
- **origin portal**: MARTECH
## What to implement
Daily AI topic candidate generation + spec scoring wired from GSC/engagement/lead data, feeding content generation.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v1 | 2026-08-09T20:30:57.085Z -->
