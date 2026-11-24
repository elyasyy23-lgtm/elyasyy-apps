# PRD — Tavakkol central hub detail page

## Product vision
 Give Tavakkol a dedicated, bilingual detail page on the central app hub so users get one stable download surface that does not depend on GitHub release CDN reachability.

## Goals
- Publish exact v1.4.23 identity: version `1.4.23`, size `37,093,105 bytes`, SHA-256 `4db1a986d2810a97f11ad20b029394338401cd57965abdc85f34d5e306982b35`.
- Expose a real APK CTA using `Tavakkol-release.apk` with `data-repo="elyasyy23-lgtm/FocusBlocker"`.
- Keep the hub card, sitemap, and root/app-scoped manifests consistent.
- Keep Persian RTL as source of truth and English as an in-place i18n swap.
- Keep the shared CSS/i18n split; do not duplicate site infrastructure.

## Users
- Persian-speaking Android users looking for Tavakkol/Parental control/keyword-blocker app.
- English users using the hub language switch.
- App update checker reading the central manifest to decide whether to prompt and where to send the user.

## Functional requirements
- `tavakkol.html` inherits the `rakaatcounter.html` shared-skin structure.
- Hub card shows `نسخهٔ ۱.۴.۲۳` / `v1.4.23`, real size, Details link, and stable APK href.
- Root `version.json`: `latestVersion: 1.4.23`, stable central `downloadUrl`, and `pageUrl` to `tavakkol.html`.
- FocusBlocker `version.json` stays aligned and gains `pageUrl` if retained as app-scoped manifest.
- Sitemap includes `tavakkol.html`.
- Validator uses the shipped APK size/hash and requires the page before passing.

## Non-functional requirements
- Mobile-first responsive; reuse `assets/site.css`.
- i18n via `window.I18N_EN` + deferred `assets/i18n.js`; cache originals before applying English.
- APK links remain real hrefs; `assets/apk-links.js` may append `?v=<tag>`.
- No invented ratings/download counts.
- No secret/token in committed files.
- No GitHub release-CDN-only link as sole route.

## User flow
Hub/card → Tavakkol detail page → Download CTA → stable `Tavakkol-release.apk` → install/update. Language switch swaps all `data-i18n` surfaces without changing hrefs.

## Edge cases
- Pages rebuild temporarily returns 404: update checker must tolerate transient 404.
- Repeated download URL must not produce a wrong “oldest build” file; stable filename + `?v=` cache bust.
- Validator with stale hash must be updated, not worked around by replacing the shipped APK.
- App-side post-tag fixes are not pushed/tagged without owner decision.

## Out of scope
- New app code release/rebuild/tag.
- New Pages repo or custom domain.
- Changing FocusBlocker app functionality or adult-domain database now.
