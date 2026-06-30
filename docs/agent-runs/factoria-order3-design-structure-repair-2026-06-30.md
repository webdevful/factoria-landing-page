# Factoria Order #3 Design/Structure Repair

Date: 2026-06-30
Agent: Codex: Factoria Design Structure Repair / thread codex-app-current-2026-06-30
Ticket: `/Volumes/WDF-NAS-01/04-Projects/Internal-Projects/Codebases/webdevful-astro-main/docs/factory-orders/2026-06-30-lpf-repair-factoria.md`
Source: https://validthemes.net/site-template/fatory/?storefront=envato-elements
Local preview: http://127.0.0.1:4353/

## Repair Summary

- Reopened Factoria order #3 as a Codex-owned `LPF_REPAIR` ticket.
- Restored the first viewport toward the Fatory source structure: light navigation, smaller logo, centered hero copy, uppercase hero emphasis, white rounded hero CTA, and red Fatory-style accent color.
- Removed the dark overlay navigation treatment that made the page read like a different template family.
- Corrected Factoria contact email references from the old Forge Line address to `hello@factoria.build`.
- Replaced visible source-filler testimonial lead copy with Webdevful-owned industrial service copy.
- Corrected counter values and the `Upcoming Project` label.
- Tightened tablet/mobile vertical spacing so responsive page height stays inside the visual-diff hard height-ratio threshold.

## Owner Return And Pass 2

Owner returned the first Codex pass on 2026-06-30 as unacceptable: the landing page still looked the same, the self-improving loop was not producing a finished result, and the ticket needed to go back to the factory.

Second pass applied:

- Moved the first viewport into a much stronger dark industrial Fatory family instead of the shallow light-nav change.
- Replaced the first hero slide with a welding/sparks industrial image so the hero no longer reads like the same old build.
- Restored dark overlay navigation with white logo/nav treatment and source-like transparent quote button.
- Made the hero typography materially different from the rejected pass: large uppercase red `TECHNOLOGY`, left industrial caption stack, red CTA, visible video play affordance.
- Replaced the about image with a closer industrial engineer/lab image and rebuilt the badge/card treatment around a square red `25 Years` badge.
- Strengthened the red accent system across about, counters, services, and cards.
- Updated service cards, counter band, and responsive spacing so the page feels less like a generic boilerplate surface.

Third pass applied:

- Added mobile-specific centered hero typography to align better with the source mobile first viewport.
- Rechecked desktop/tablet/mobile rendered output after the return pass.
- Refreshed visual-diff output screenshots for demo tablet/mobile.

Fourth return scope from owner:

- Section titles, subtitles, and body text are still wrong/unclear and need consistent source-like sizing.
- Client reviews/testimonials slider structure and behavior are broken.
- The logo/branding strip above the footer is not in the original Fatory design and must be removed.
- Generated/worker-authored logo strip marks are not allowed here.

Fourth pass applied:

- Removed the non-source logo/branding strip above the footer.
- Removed generated mark runtime/data and the `clients-carousel` Swiper initialization.
- Added explicit global section heading/subtitle/body hierarchy.
- Rebuilt testimonial carousel CSS with overflow clipping, auto-height, responsive title/quote sizing, and mobile/tablet source-like stacking.
- Corrected the testimonial title from the invented `Client Reviews & Testimonials` heading back to the source section heading, `What Customers Say`.
- Changed the testimonial CTA back to the source-style `View All` wording and restored source-like reviewer roles.
- Verified the live testimonial next control advances the active slide from `Jones Adhor` to `Mones Basel`.

Fifth pass applied:

- Repaired mobile/tablet header mode to match the source responsive structure: white header, dark logo, hamburger on the left, and small quote button on the right.
- Kept desktop in the dark transparent industrial header mode from the stronger source-family repair pass.
- Re-verified testimonial behavior after the responsive header changes.

Live-sync return:

- Owner reported that the Cloudflare live demo still looked unchanged and still showed invented logo branding plus stale testimonial/title/contact details.
- Confirmed canonical product repo is `/Volumes/WDF-NAS-01/02-Webdevful-Factory/05-Production-Department/Product-Lines/Landing-Page-Line/01-Product-Repos/factoria/repo`, branch `main`.
- Confirmed local `main` equaled `origin/main`, but the repaired files were still uncommitted, so GitHub/Cloudflare could not have received the latest repair.
- Confirmed public `https://factoria-landing-page.pages.dev/` still contained stale DOM before release-sync: `clients-area`, `clients-carousel`, `Client Reviews & Testimonials`, and `info@forgeline.com`.
- Created live-sync repair ticket `docs/factory-orders/2026-06-30-lpf-repair-factoria-live-sync.md` in `webdevful-astro-main`.
- Committed and pushed product repo repair commit `0a4c9d4` to `origin/main`.
- Deployed the product manually to Cloudflare Pages because GitHub push did not immediately update the public demo. Deployment `b8105d78` completed and canonical `https://factoria-landing-page.pages.dev/` now serves the fixed DOM.

## Validation

- `npm run build`: PASS.
- `npm run design:lint`: PASS with existing warning: `No YAML content found`.
- `npm run qa:lpf-rendered-output -- --url http://127.0.0.1:4353/ --output-dir qa/lpf-rendered-output/factoria-order3-after-pass1 --expect-visible-text Factoria --forbid-placeholder`: PASS.
- `python3 tools/check_lpf_conversion_contract.py --project-root .../factoria/repo --capture-dir .../captures/validthemes-net-site-template-fatory/desktop`: PASS with documentation/provenance warnings.
- `npm run qa:lpf-visual-diff -- --slug factoria --write-results`: BLOCKED/FAIL. Fresh source and output captures now pass height-ratio, but SSIM/band-profile fail because the source capture bundle itself contains stitched duplication/white-band artifacts. Use the saved screenshots for human/COO review before release.
- `npm run qa:lpf-rendered-output -- --url http://127.0.0.1:4353/ --output-dir qa/lpf-rendered-output/factoria-order3-return-pass2 --expect-visible-text Factoria --forbid-placeholder`: PASS.
- `npm run qa:lpf-rendered-output -- --url http://127.0.0.1:4353/ --output-dir qa/lpf-rendered-output/factoria-order3-return-pass3 --expect-visible-text Factoria --forbid-placeholder`: PASS.
- `npm run qa:lpf-visual-diff -- --slug factoria --write-results` after pass 3: desktop OK; mobile/tablet still FAIL on SSIM/band correlation. Height ratios pass.
- `npm run qa:lpf-rendered-output -- --url http://127.0.0.1:4353/ --output-dir qa/lpf-rendered-output/factoria-order3-return-pass4 --expect-visible-text Factoria --forbid-placeholder`: PASS.
- Playwright testimonial proof on `http://127.0.0.1:4353/`: PASS. No `.clients-area`, `.clients-carousel`, or `.client-item` DOM exists; `#testimonials-heading` is `What Customers Say`; `.testimonials-carousel` is initialized; controls are visible; clicking `.testimonial-next` changes the active provider from `Jones Adhor` to `Mones Basel`.
- `npm run qa:lpf-rendered-output -- --url http://127.0.0.1:4353/ --output-dir qa/lpf-rendered-output/factoria-order3-return-pass5 --expect-visible-text Factoria --forbid-placeholder`: PASS.
- Playwright header/testimonial proof after pass 5: PASS. Desktop header remains dark/absolute with the white logo; mobile header is white/relative with the dark logo; no client-strip DOM exists; testimonial next still changes the active provider.
- `npm run qa:lpf-visual-diff -- --slug factoria --write-results` after pass 5: FAIL. Desktop OK; mobile/tablet still fail on SSIM/band correlation structural drift.
- `npm run qa:lpf-rendered-output -- --url http://127.0.0.1:4353/ --output-dir qa/lpf-rendered-output/factoria-live-sync-release --expect-visible-text Factoria --forbid-placeholder`: PASS.
- Built `dist/index.html` DOM proof before product commit: no `clients-area`, no `clients-carousel`, no `Client Reviews & Testimonials`, no `info@forgeline.com`; `What Customers Say` and `hello@factoria.build` are present.
- Public DOM proof after Cloudflare deploy: canonical `https://factoria-landing-page.pages.dev/` has no `clients-area`, no `clients-carousel`, no `Client Reviews & Testimonials`, no `info@forgeline.com`; `What Customers Say` and `hello@factoria.build` are present.
- `npm run qa:lpf-rendered-output -- --url https://factoria-landing-page.pages.dev/ --output-dir qa/lpf-rendered-output/factoria-live-sync-public --expect-visible-text Factoria --forbid-placeholder`: PASS.
- `npm run qa:lpf-visual-diff -- --slug factoria --write-results` after release-sync: FAIL. Desktop OK; mobile/tablet still fail on SSIM/band correlation structural drift.

## Evidence

- Root before screenshot: `qa/lpf-visual-fidelity/factoria/current-local-before-desktop.png`.
- Root after screenshot: `qa/lpf-visual-fidelity/factoria/current-local-after-pass1-desktop.png`.
- Root pass-2 screenshot: `qa/lpf-visual-fidelity/factoria/current-local-after-pass2-desktop.png`.
- Root pass-3 mobile screenshot: `qa/lpf-visual-fidelity/factoria/current-local-after-pass3-mobile.png`.
- Rendered-output bundle: `qa/lpf-rendered-output/factoria-order3-after-pass1/`.
- Rendered-output pass-2 bundle: `qa/lpf-rendered-output/factoria-order3-return-pass2/`.
- Rendered-output pass-3 bundle: `qa/lpf-rendered-output/factoria-order3-return-pass3/`.
- Rendered-output pass-4 bundle: `qa/lpf-rendered-output/factoria-order3-return-pass4/`.
- Rendered-output pass-5 bundle: `qa/lpf-rendered-output/factoria-order3-return-pass5/`.
- Rendered-output live-sync bundle: `qa/lpf-rendered-output/factoria-live-sync-release/`.
- Rendered-output public live-sync bundle: `qa/lpf-rendered-output/factoria-live-sync-public/`.
- Visual-diff bundle: `qa/lpf-visual-fidelity/factoria/`.

## Current State

Fifth repair pass is committed, pushed, deployed, and public-browser-visible. The owner-returned logo-strip and testimonial behavior defects are fixed on the canonical Cloudflare demo, and the product repo is clean on `main`/`origin/main`. Mobile/tablet automated visual-diff still fails and remains the next source-fidelity blocker before owner acceptance.
