# Capability: Verified Transactional Email Infra
- **key**: `transactional_email_infra`
- **category**: email
- **origin portal**: MARTECH
## What to implement
Native Lovable Emails (branded) on verified domain (notify.mail.help.innovexsis.com) with SPF/DKIM/DMARC, unsubscribe tokens, suppression list, and queue-based sends. Resend is fully retired — no fallback.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v3 | 2026-08-09T20:31:10.013Z -->
