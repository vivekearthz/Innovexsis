# Master Patch v50 — Per-Host SEO Identity + Official Email Correction

Master: MARTECH. Audience: all main portals, sub-portals and slave portals. Supersedes v49 (v48/v49 still apply).

## 1. Duplicate titles are a defect (mandatory)
Every host served by a shared "/" route MUST emit its OWN head metadata. A static `head()` on a multi-host route makes search and AI engines collapse the portals into duplicates and suppress all but one.

Required per host / per portal:
- Unique `<title>` (< 60 chars, primary keyword first, never repeated anywhere in the fleet).
- Unique `<meta name="description">` (< 160 chars).
- SELF-REFERENCING `<link rel="canonical">` and `og:url` pointing at that host's own origin — never at the master domain.
- Unique `og:title` / `og:description` plus `og:type` and `twitter:card`.
- Per-host JSON-LD: Organization + WebSite with the host's own `@id` and `url`. Do not reuse the master's graph.

Implementation reference (master): `src/lib/portal-seo.ts` holds a keyed identity map; the route resolves the host in `beforeLoad`, passes the product key through `loader`, and `head({ loaderData })` builds the tags. Single-product portals hardcode their own identity.

## 2. Official contact email (mandatory)
The ONLY valid public Innovexsis address is `director@innovexsis.com`.

These mailboxes DO NOT EXIST and must be purged from every CTA, contact block, footer, listing, email template, WhatsApp template, JSON-LD and social profile:
`hello@`, `help@`, `info@`, `support@`, `contact@`, `admin@`, `sales@` (all @innovexsis.com).

Add a build/audit guard: any occurrence of a forbidden address fails the content check and is auto-replaced with `director@innovexsis.com`.

## 3. Loopback + self-heal (mandatory)
After applying 1-2: republish via REPUBLISH_HOOK_URL, then ACK to the master with the emitted title/canonical for your host so the master's fleet SEO audit can verify uniqueness. The weekly `seo-audit-weekly` run re-checks and re-dispatches on drift, with zero human intervention.

## Required env (already common)
MASTER_HOST, MASTER_SYNC_SECRET, PRODUCT (=portal_key), REPUBLISH_HOOK_URL.


<!-- applied-by: MARTECH master | version: v50 | reason: resume-context-fleet-refresh | at: 2026-08-11T05:09:40.591Z -->
