# AGENTS.md — elyasyy-apps staging (Tavakkol v1.4.24 published / app HOLD)

## Project
Central GitHub Pages hub for the owner's Android apps: `https://elyasyy23-lgtm.github.io/elyasyy-apps/`.
Local staging repo: `/data/data/com.termux/files/home/storage/shared/ZYVO/session-20261120-085437/elyasyy-apps-staging`.
Repository: `elyasyy23-lgtm/elyasyy-apps`, branch `main`. Current HEAD: `63eb339 Update Tavakkol hub pages to v1.4.24`.

## Key files
- `index.html`: hub landing page, 4 app cards, search, i18n.
- `tavakkol.html`: Tavakkol detail page. Persian fallback is source of truth; English `window.I18N_EN` must stay version/date consistent.
- `version.json`: root Tavakkol manifest, `latestVersion: 1.4.24`, central `downloadUrl` + `pageUrl`.
- `Tavakkol-release.apk`: stale tracked v1.4.23 mirror (`37093105`, `4db1a986…`); do not replace without explicit owner decision.
- `assets/site.css`, `assets/i18n.js`, `assets/apk-links.js`: shared assets, never duplicate per app.
- `TASK.md`: current checkpoint/registry.
- `PRD.md`, `PROJECT_PLAN.md`: broader plan records.

## Commands
- Hub validator: `node /data/data/com.termux/files/usr/tmp/zyvo/htmlcheck/check-hub.mjs`
- Tavakkol page validator: `python3 /data/data/com.termux/files/usr/tmp/zyvo/htmlcheck/validate-tavakkol.py /data/data/com.termux/files/home/storage/shared/ZYVO/session-20261120-085437/elyasyy-apps-staging/tavakkol.html`
- Staging validator: `python3 /data/data/com.termux/files/usr/tmp/zyvo/htmlcheck/validate-staging.py /data/data/com.termux/files/home/storage/shared/ZYVO/session-20261120-085437/elyasyy-apps-staging`
- Redirect validator: `node /data/data/com.termux/files/usr/tmp/zyvo/htmlcheck/check-redirects.mjs`
- Watcher syntax: `bash -n /data/data/com.termux/files/home/watch-tavakkol.sh`
- APK facts: `stat -c '%s %n' Tavakkol-release.apk`; `sha256sum Tavakkol-release.apk`
- GitHub release facts (when `gh api` is unauthenticated): `TOKEN=$(sed -E 's#https://[^:]+:([^@]+)@github.com#\1#' ~/.git-credentials | tail -1); curl -s -H "Authorization: token $TOKEN" -H "Accept: application/vnd.github+json" "https://api.github.com/repos/elyasyy23-lgtm/FocusBlocker/releases/tags/v1.4.24"`

## Current state (2026-11-22)
- Shipped release is `v1.4.24`; APK `/storage/emulated/0/Download/Tavakkol-release.apk` is `37093010` / `81dec9efdc80fd6eaa9e702bef9faaf721a87959633ea32bddd22dc37da65fff` and installed on the phone.
- Tracked git tree is clean; untracked records remain: `AGENTS.md`, `FocusBlocker/`, `PRD.md`, `PROJECT_PLAN.md`, `TASK.md`. Do not fold them into any commit.
- Published commit `63eb339` changed only `index.html` + `tavakkol.html` (`2 files changed, 23 insertions(+), 23 deletions(-)`) and pushed `43c0224..63eb339  main -> main`.
- Live Pages verified after push: `LIVE_OK`; hub `21112` bytes with `v1.4.24` present / `v1.4.23` absent; Tavakkol page `36073` bytes with `PAGE_STALE` all zeros; live `version.json` = `1.4.24` with central `downloadUrl` + `pageUrl`.
- Final local checks before publish: `git diff --check` OK; stale version/date/hash tokens in `tavakkol.html` count 0; `INLINE_SCRIPTS_OK 5` after excluding `application/ld+json`.
- Validator scripts are currently unavailable under `$TMPDIR/zyvo/htmlcheck`; older failure notes are historical only. Do not recreate or guess validators. Run only if restored/provided.
- No APK replacement, app rebuild, re-tag, or release replacement has been done after the shipped v1.4.24 release.

## Decisions / rules
- HOLD is active. Treat green CI/build and verified APK as proof of the shipped release only, not authorization for post-release work.
- No APK/source/release/tag changes without explicit owner decision.
- Before any push, run all validators, grep for `1.4.23|۱.۴.۲۳|37093105|۳۷٬۰۹۳٬۱۰۵|4db1a986|21 November 2026|۲۱ نوامبر ۲۰۲۶`, and confirm fresh `git diff/status`.
- Use `releases/latest/download/<asset>`-style stable filenames and central Pages APK hosting; no per-app Pages sites.
- Persian/RTL markup is source of truth; shared `assets/` only.
- Historical notes that say `v1.4.23`, `8df48d7`, `74eab8d`, or "FINAL PRODUCTION BUILD REQUESTED" are context only; do not infer authorization from them.
- Owner-run exact git command blocks delegate only that block, not later fixes.
- 2026-11-22 owner chose `local-fix-only` (reply `2`): local page/checker fixes were completed first; no push, publish, live verify, APK/app/rebuild/tag/release change authorized at that time.
- 2026-11-22 owner then chose `1` = publish hub now: explicit authorization to commit + push ONLY `index.html` and `tavakkol.html` to `elyasyy-apps` `main`, then verify live Pages. Do NOT commit `AGENTS.md`, `FocusBlocker/`, `PRD.md`, `PROJECT_PLAN.md`, `TASK.md`, or the stale `Tavakkol-release.apk`; no APK/app/rebuild/tag/release change.
- 2026-11-22 owner replied `4` = local-only record update; checkpoint/memory only. No APK, source, hub, rebuild, re-tag, release, push, tag, or CI action authorized.
