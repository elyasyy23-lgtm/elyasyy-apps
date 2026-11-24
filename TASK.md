# TASK.md — Tavakkol v1.4.24 central hub published / app HOLD

GOAL: Keep the shipped Tavakkol v1.4.24 release and installed APK untouched; central-hub pages are published and live-verified; HOLD remains for explicit owner decisions on APK/app/rebuild/re-tag/release work.

PLAN: `PROJECT_PLAN.md` and `PRD.md` in this directory remain the broader build plan registry; this file is the current checkpoint.

## Verified shipped state
- GitHub release `v1.4.24`: `Tavakkol v1.4.24`, not draft, not prerelease, published `2026-11-22T10:16:59Z`.
- Release asset `Tavakkol-release.apk`: size `37093010`, sha256 `81dec9efdc80fd6eaa9e702bef9faaf721a87959633ea32bddd22dc37da65fff`, downloads 2.
- Verified local copy: `/storage/emulated/0/Download/Tavakkol-release.apk` = same size/hash. Do not modify, replace, download again, or re-tag.
- Staged local APK is stale v1.4.23 mirror: `37093105` / `4db1a986d2810a97f11ad20b029394338401cd57965abdc85f34d5e306982b35`; tracked and not gitignored. Do not replace without explicit owner decision.
- `version.json` = `latestVersion: 1.4.24`, central `downloadUrl`, central `pageUrl`.
- Repo `elyasyy-apps-staging` is on `main` at `63eb339` (published commit `Update Tavakkol hub pages to v1.4.24`); tracked tree is clean, with only untracked local records/history remaining.

## Local work done
- [x] Re-read handoff files: `TASK.md`, `AGENTS.md`, vault continuation, global `~/AGENTS.md`, and `tavakkol-post-release-handoff` skill.
- [x] Verified release facts with read-only GitHub API; `gh api` failed unauthenticated, curl with token from `~/.git-credentials` succeeded.
- [x] Verified Download APK and staged APK by size + sha256.
- [x] Ran local gates: `HUB_OK cards=4 i18n=45 repos=4`, `REDIRECTS_OK 62/62`, `bash -n ~/watch-tavakkol.sh` OK.
- [x] Owner chose `local-fix-only` (reply `2`): local checker/page fixes authorized; no push, publish, live verify, APK/app/rebuild/tag/release change.
- [x] Aligned `index.html` hub card and all `tavakkol.html` Persian fallback + English i18n fields to `v1.4.24` / `2026-11-22`.
- [x] Captured final diff/stat/status: `2 files changed, 23 insertions(+), 23 deletions(-)` in `index.html` + `tavakkol.html`.
- [x] Final stale-token counts in `tavakkol.html` are all 0 for `1.4.23`, `۱.۴.۲۳`, `37093105`, `۳۷٬۰۹۳٬۱۰۵`, `4db1a986`, `21 November 2026`, `۲۱ نوامبر ۲۰۲۶`, `2026-11-21`.
- [x] `git diff --check` OK; `INLINE_SCRIPTS_OK 5` after excluding `application/ld+json`.
- [x] Owner then chose `1` = publish hub now; commit `63eb339` pushed to `elyasyy-apps` `main`.
- [x] Live Pages verified: `LIVE_OK` with v1.4.24 tokens, zero stale v1.4.23/date/hash tokens, and central `version.json` = `1.4.24`.
- [x] Vault note written: `2026-11-22 Tavakkol hub publish verification.md`.

## Post-publish state
- [x] `tavakkol.html` English i18n and Persian fallback/release fields are all v1.4.24 / `2026-11-22`.
- [x] `index.html` hub card version is v1.4.24.
- [x] Final local checks: `git diff --check` OK, `INLINE_SCRIPTS_OK 5` (JSON-LD excluded), `git diff --stat` 23/23.
- [ ] Validator scripts are currently unavailable under `$TMPDIR/zyvo/htmlcheck`; do not recreate or guess them. Run only if restored/provided.
- [ ] Staged `Tavakkol-release.apk` remains stale; no APK copy/replacement performed.
- [x] Hub commit/push and live Pages verification completed; app rebuild, re-tag, release replacement, and APK replacement remain unauthorized.

## Key decisions
- HOLD is active: green CI/build and verified APK prove the shipped release only; they do not authorize post-release fixes.
- No APK/source/release/tag changes without explicit owner decision.
- Use published GitHub release metadata as source of truth, not local mirror files or stale handoff docs.
- Treat `TAVAKKOL_APP_SIDE_FIX_PROPOSAL.md`, vault continuation, and older `v1.4.23` sections in `AGENTS.md` as historical/proposal context only.
- "Continue" authorizes local records/checkpoint/memory only, then STOP and ask for explicit decisions.

## Current gates and evidence
- Final post-publish checks:
  - Published commit: `63eb339 Update Tavakkol hub pages to v1.4.24`; pushed `43c0224..63eb339  main -> main`.
  - Final tracked state: clean; untracked `AGENTS.md`, `FocusBlocker/`, `PRD.md`, `PROJECT_PLAN.md`, `TASK.md` only.
  - Live `LIVE_OK`: hub `21112` bytes, `v1.4.24` present / `v1.4.23` absent; Tavakkol page `36073` bytes.
  - Live page: `PAGE_STALE` all zeros; `PAGE_v1.4.24 10`, `PAGE_۱.۴.۲۴ 9`, `PAGE_2026-11-22 3`, `PAGE_۲۲ نوامبر ۲۰۲۶ 3`.
  - Live `version.json`: `1.4.24`, central `downloadUrl` + `pageUrl`.
- Historical gate evidence only (before final local edits): `HUB_OK cards=4 i18n=45 repos=4`, `REDIRECTS_OK 62/62`, `bash -n ~/watch-tavakkol.sh` OK.
- Validator scripts are currently unavailable; the older `validate-tavakkol.py` / `validate-staging.py` failure notes are historical and must not be recreated or guessed.
- `git check-ignore -v Tavakkol-release.apk` => `CHECK_IGNORE_RC=1` (tracked, not ignored).

- 2026-11-22 owner replied `4` = local-only record update; checkpoint/memory only, no outward/app change authorized.

NOW: central-hub v1.4.24 publication is committed, pushed, and live-verified. Owner chose local-only record update; HOLD remains for APK/app/source/rebuild/re-tag/release work. STOP and wait for an explicit new owner decision before any outward action.
