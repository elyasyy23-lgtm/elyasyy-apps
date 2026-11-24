# PROJECT_PLAN — Tavakkol on central elyasyy-apps hub

Track: quick (single detail page + hub surface updates on an existing multi-page site)
Goal: publish Tavakkol v1.4.23 on the canonical central hub with a dedicated page, correct APK mirror, and central update metadata.

- [x] Plan file created
- [x] PRD created
- [x] Confirm verified release APK and exact identity (v1.4.23 / 37093105 / 4db1a986…)
- [x] Mirror verified APK into hub staging at stable filename
- [x] Create `tavakkol.html` from the shared-skin detail-page template
- [x] Clean mixed-language tokens in `tavakkol.html` (codepoint-exact minimal edits)
- [x] Validate `tavakkol.html` with `validate-tavakkol.py` (`TAVAKKOL_PAGE_OK keys=115 used=112 scripts=5 apk_ctas=3`)
- [x] Update hub index card (version, size, details link)
- [x] Update root `version.json` (`latestVersion`, `downloadUrl`, `pageUrl`)
- [x] Update FocusBlocker app-scoped `version.json` if retained
- [x] Update `sitemap.xml`
- [x] Update staging validator expectations
- [x] Run local validation (structure, i18n, scripts, hashes, redirects)
  - `STAGING_OK base=https://elyasyy23-lgtm.github.io/elyasyy-apps/ i18n_keys=461 scripts=27`
  - `HUB_OK cards=4 i18n=45 repos=4`
  - `REDIRECTS_OK 62/62`
- [x] Add/verify Tavakkol watcher using `~/gh-release-download.sh`
- [ ] Commit and push hub changes
- [ ] Verify live Pages URLs, `version.json`, and APK byte identity
- [ ] Report exact central page URL and next owner decision for app-side post-tag fixes

## Decisions
- Central hub is `https://elyasyy23-lgtm.github.io/elyasyy-apps/`; no new Pages repo.
- APK filename stays `Tavakkol-release.apk`; cache bust via `?v=` only.
- Ownership note: app-side post-tag fixes stay local until the owner chooses rebuild/re-tag vs next version.
