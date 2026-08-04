# Master Patch v44 — Email-Only Journey + GitHub Fleet Durability

Master: MARTECH. Audience: master, all sub-portals, all slave portals, all
independent PWA hosts. v13 / v29 / v40 / v41 / v42 still apply.

## 1. Email-only verification window
Until 2026-08-27, registration and sign-in collect and verify only the email
code. Hide phone and WhatsApp-code inputs, skip phone validation, and do not
invoke WhatsApp, SMS, or alternate-phone delivery. Keep existing credentials
and templates untouched so the prior flow can resume after the window.

## 2. Customer-journey durability
- Persist non-secret registration progress across refresh/OAuth return.
- Isolate OTP rate limits by purpose and give transactional OTP mail bounded
  exponential retry priority over broadcasts.
- Retry session verification before rejecting a completed managed OAuth login.
- Activate paid access only after provider-side subscription confirmation.
- Keep clean sign-out and router navigation from the v41 contract.

## 3. GitHub continuity after workspace moves
- Canonical owner identity: vivekearthz@gmail.com / GitHub login vivekearthz.
- Preserve each portal's own repository mapping from the private fleet registry.
- Install both born-wired routes in every mapped slave repository.
- On each durability sweep: restore canonical mappings first, reconcile current
  renames/transfers, force-enroll agents, verify patch SHA, retry failures, back
  up the repaired registry, then republish the whole fleet.
- Repository/API durability is independent of the Lovable project-settings
  GitHub App. A settings-level account mismatch still requires re-authorizing
  that app as the same GitHub user; never copy or expose secret values.

## 4. Loopback
After applying this patch, run master-sync, ACK pending config commands, emit a
heartbeat containing policy v44, and republish. The master rechecks repository
and patch presence and retries drift automatically.

## Required env (already common)
MASTER_HOST, MASTER_SYNC_SECRET, PRODUCT (=portal_key), REPUBLISH_HOOK_URL.
Master-only durability credentials remain server-side.


<!-- applied-by: MARTECH master | version: v44 | reason: loopback-self-heal | at: 2026-08-04T21:45:12.969Z -->
