# Master Patch v56 — Total Master Authority, Two-Way Consolidation Ledger & Current-Repo-Only Publishing

Master: MARTECH (marcomm). Audience: master portal, every sub-portal and every slave portal. Supersedes v55 (all earlier patches still apply).

## 1. The master has FULL authority — master always wins
- Every portal under the owner's GitHub account is a SLAVE of MARTECH by default. There is no opt-out and no partial enrollment.
- On every conflict between a slave value and the master value (policy, config, connector slot names, sender identity, AI ladders, SEO identity, cadence, templates), the MASTER VALUE WINS and is force-written back to the slave.
- Slaves may only ADD net-new innovations. Those are pulled up, consolidated and then re-published to the whole fleet by the master — never adopted locally in isolation.

## 2. Auto-enrollment of any NEW portal (zero human steps)
- Every sweep lists all repositories under the owner account, detects any project not present in the master registry, and enrolls it as an active slave: registry row + linked brand + born-wired agent files + current patch + republish.
- Newly created projects therefore join the fleet on the next sweep with nothing to paste and no repo to create by hand.

## 3. Two-way consolidation into ONE canonical sheet
- PULL: every portal reports its capabilities, best-performing strategies and configs upstream.
- CONSOLIDATE: the master merges them into a single canonical catalog (highest version wins, master wins ties), recording origin portal and which portals already hold each capability.
- REPUBLISH: the consolidated sheet is pushed back down to EVERY portal as capability specs + policy bundle, so all portals converge on the union of the fleet's best solutions.

## 4. CURRENT GitHub repositories only
- The registry keeps exactly one current repository per active portal, pinned to the canonical map.
- Legacy/renamed/duplicate repository links (from workspace moves) are archived into audit logs and cleared. The admin surface lists only live repositories, and all code publishing targets those current repos only.

## 5. Patch-version convergence loop (no drift allowed)
- The sweep re-applies the current patch to every mapped slave with retries, then loopback-verifies the file exists on the slave branch.
- It repeats until 100% of active portals report `patch_status = verified` at the current version, or the bounded pass limit is hit; laggards are escalated to the self-heal ladder and retried on the next 02:30 IST run.
- After convergence the master forces a fleet-wide republish so every portal is live on the same version.

## Required environment
MASTER_HOST, MASTER_SYNC_SECRET, PRODUCT (= portal_key), REPUBLISH_HOOK_URL. `LOVABLE_API_KEY` remains NOT required anywhere (v55 credit freedom stands).


<!-- applied-by: MARTECH master | version: v56 | reason: cron:fleet-identity-drift | at: 2026-08-20T02:28:46.370Z -->
