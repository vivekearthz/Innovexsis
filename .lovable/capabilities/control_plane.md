# Capability: Master Control Plane
- **key**: `control_plane`
- **category**: governance
- **origin portal**: MARTECH
## What to implement
portal_directives (feature flags/kill switches) + portal_commands (remote execution incl. republish) delivered via the sync pull.
## How to apply
1. Read your inbound `controlPlane` + `commands` from the master sync pull.
2. Implement this capability using your existing master-provided connectors
   (AI via the master gateway, WhatsApp via Emovur, email via native Lovable Emails) — never
   hold provider keys locally.
3. Honour the master policy bundle (self-heal, fallback, opt-out, IST cadence,
   contact block + branded short links, feature deep-link CTAs).
4. After applying, report the capability back via
   `POST /api/public/hooks/capability-report` so the gap matrix closes.
<!-- federated-by: MARTECH master | v1 | 2026-08-09T20:31:17.029Z -->
