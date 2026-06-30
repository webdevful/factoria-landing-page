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

## Slider Interactivity Return

Owner returned Factoria again on 2026-06-30 for broken slider behavior, broken testimonial slider icon, and stale detail-page text/tag metadata. Created factory ticket `docs/factory-orders/2026-06-30-lpf-repair-factoria-slider-interactivity.md` in `webdevful-astro-main`.

Changes applied:

- Updated hero, portfolio, and testimonial slider arrow controls from legacy `fas` classes to current Font Awesome `fa-solid` angle icons.
- Changed hero, portfolio, and testimonial Swiper setups to use deterministic `rewind` navigation so visible next/previous controls do not dead-end.
- Changed Swiper autoplay to stop after user interaction so manual navigation is not overridden by the autoplay timer.
- Kept the testimonial carousel as one slide per view with source-style left-aligned arrow navigation.
- Updated Webdevful catalog detail metadata in `src/data/landing-pages.ts` to remove stale sponsor/client strip and non-existent team/client carousel claims, and to list actual Swiper rewind interactions.

Validation:

- Product `npm run build`: PASS.
- Product `npm run design:lint`: PASS with existing warning: `No YAML content found`.
- Playwright local slider proof on `http://127.0.0.1:4353/`: PASS. Hero next/previous changed active heading; portfolio next/previous changed active project; testimonials next/previous changed active reviewer.
- Testimonial icon proof: `.testimonial-next i` uses `fa-solid fa-angle-right`, Font Awesome 7 Free renders the angle glyph, and the button is not disabled.

## Visual Fidelity Continuation

Owner asked to continue after the slider/tag/preview repair. The remaining blocker was the source-backed mobile/tablet visual-fidelity bundle.

Changes applied:

- Added an exact `768px` tablet breakpoint repair so the factory tablet viewport no longer inherits the phone layout.
- Restored source-like tablet rhythm for the work-process and blog card grids.
- Changed the tablet portfolio band back toward the source structure: white section background with dark project cards instead of a full black section.
- Refreshed the source/output evidence with clean browser full-page captures to avoid the earlier stitched source hero/background artifact.

Validation:

- Product `npm run build`: PASS.
- Root `npm run qa:lpf-visual-diff -- --slug factoria --write-results`: PASS. Desktop `h-ratio 0.94 / band 0.75 / ssim 0.37`; mobile `h-ratio 0.92 / band 0.66 / ssim 0.22`; tablet `h-ratio 0.87 / band 0.49 / ssim 0.25`.
- Root `npm run qa:lpf-rendered-output -- --url http://127.0.0.1:4361/ --output-dir qa/lpf-visual-fidelity/factoria/rendered-output --expect-visible-text Factoria --forbid-placeholder`: PASS.
- Root `npm run qa:lpf-visual-fidelity -- --slug factoria --product-repo .../factoria/repo --rendered-url http://127.0.0.1:4361/ --expect-visible-text Factoria`: PASS.

## Team Social Bar Return

Owner returned Factoria section 7 on 2026-06-30 because the Team Members cards did not preserve the source social bar. The original Fatory screenshot shows a white social media bar overlapping the bottom of each team image/card; the current Factoria page rendered loose icons below the image without the overlapping bar.

Changes applied:

- Repaired `.team-item .social` into a real inset white bar with a negative top margin, shadow, centered layout, and overlap against the team image card.
- Lifted the team name/role gradient overlay so the social bar does not cover the member text.
- Preserved the existing Font Awesome social icons: Facebook, X/Twitter, and Instagram.
- Added `qa/lpf-source-design-contracts/factoria.json` so the self-improving loop now checks the team social-bar structure and fails if it regresses into a loose icon row.

Validation:

- Product `npm run build`: PASS.
- Product `npm run design:lint`: PASS with existing warning: `No YAML content found`.
- Root `npm run qa:lpf-memory-loop -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-team-social-bar.md`: PASS.
- Root `npm run qa:lpf-dispatch-preflight -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-team-social-bar.md`: PASS.
- Source-design contract: `LPF_REQUIRE_SOURCE_TYPOGRAPHY=1 LPF_LANDING_PAGE_SLUG=factoria python3 .../tools/check_lpf_conversion_contract.py --project-root .../factoria/repo --landing-page-slug factoria`: PASS.
- Local browser geometry proof on `http://127.0.0.1:4372/`: PASS. First team card social bar overlaps the thumbnail by `30px`, renders white, has a shadow, and keeps three Font Awesome icons.

## Team Heading Divider And Hover Return

Owner returned the same Team Members section on 2026-06-30 because the source heading divider decoration was still missing and the team-card hover effect behaved too fast and unlike the original Fatory hover.

Source/current measurements:

- Live Fatory source Team Members H2 has red pseudo-elements under the title: `::before` width `40px`, `::after` width `5px`, both `2px` high and red.
- Previous Factoria public H2 had no pseudo-elements.
- Live Fatory source hover fades member info with `0.65s ease-in-out` and slides descriptive overlay text over a darkened image.
- Previous Factoria public hover used a fast `0.3s` full-card opacity overlay that completed almost immediately.

Changes applied:

- Added source-style red H2 divider pseudo-elements to the Team Members section.
- Preserved eyebrow/title/body vertical order after adding the divider.
- Changed team hover to use a darkening image pseudo-overlay, slower `650ms ease-in-out` timing, and a sliding transparent text overlay instead of a fast full-card blackout.
- Extended `qa/lpf-source-design-contracts/factoria.json` so the self-improving loop now enforces heading divider pseudo-elements, slower hover timing, transparent overlay behavior, and forbids the old full-card overlay background.

Validation:

- Product `npm run build`: PASS.
- Product `npm run design:lint`: PASS with existing warning: `No YAML content found`.
- Source-design contract: `LPF_REQUIRE_SOURCE_TYPOGRAPHY=1 LPF_LANDING_PAGE_SLUG=factoria python3 .../tools/check_lpf_conversion_contract.py --project-root .../factoria/repo --landing-page-slug factoria`: PASS.
- Local browser proof on `http://127.0.0.1:4374/`: PASS. The eyebrow remains above the title, the description remains below the title, H2 divider pseudo-elements are `40px + 5px`, hover is intermediate at `250ms` (`infoOpacity 0.692`, `overlayOpacity 0.308`) and completes by `900ms`.

## Global Heading Typography Loop

Owner returned Factoria again on 2026-06-30 because the horizontal red title decoration and source typography were still not applied page-wide. The previous heading repair only codified the Team Members H2, while the original Fatory source uses the `.site-heading h2` system across repeated section headings.

Source measurements:

- Live/source Fatory repeated section headings (`Work Process`, `Latest Work`, `Team Members`, `Latest News`) use Inter, `52px`, weight `600`, line-height `62.4px`, `1px` letter spacing, `text-transform: capitalize`, `padding-bottom: 20px`, and centered H2 pseudo-elements: `::before` width `40px`, `::after` width `5px`, both `2px` high and red `rgb(255, 53, 20)`.
- Previous Factoria global `.section-header h2` used the smaller Poppins/Nunito-derived scale and had no global pseudo-elements; only `.team-area .section-header h2` carried the prior divider.

Changes applied:

- Changed the page typography tokens to source-derived Inter for display and body text.
- Updated body copy to the source-like `15px` / `30px` baseline.
- Rebuilt global `.section-header`, `.section-tag`, `.section-header h2`, and `.section-desc` around the source `.site-heading` measurements.
- Added the red 40px + 5px pseudo-divider to every repeated `.section-header h2` section title.
- Removed the Team-only H2 divider override so the title system is now page-level instead of section-level.
- Extended `qa/lpf-source-design-contracts/factoria.json` to enforce global section-heading typography/divider checks and forbid the previous undersized Poppins/Nunito heading system.

Validation:

- Product `npm run build`: PASS.
- Product `npm run design:lint`: PASS with existing warning: `No YAML content found`.
- Root `npm run qa:lpf-memory-loop -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-global-heading-typography-loop.md`: PASS. STAMP MLP ticket=2026-06-30-lpf-repair-factoria-global-heading-typography-loop lane=LPF at=2026-06-30 digest=a518d180.
- Root `npm run qa:lpf-dispatch-preflight -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-global-heading-typography-loop.md`: PASS. STAMP DPP ticket=2026-06-30-lpf-repair-factoria-global-heading-typography-loop lane=LPF at=2026-06-30 digest=f59f6980.
- Source-design contract: `LPF_REQUIRE_SOURCE_TYPOGRAPHY=1 LPF_LANDING_PAGE_SLUG=factoria python3 .../tools/check_lpf_conversion_contract.py --project-root .../factoria/repo --landing-page-slug factoria`: PASS.
- Local browser proof on `http://127.0.0.1:4375/`: PASS. Desktop `services`, `process`, `portfolio`, `team`, and `blog` section H2s render Inter `52px`, weight `600`, line-height `62.4px`, `1px` letter spacing, source red pseudo-divider `40px + 5px`, and block-level eyebrow above title. Mobile keeps Inter, weight `600`, red pseudo-divider, and source order with responsive `32px` headings.

## Testimonial Slider Icon And Quote Placement Return

Owner returned Factoria again on 2026-06-30 because the testimonials slider arrow icons did not match the source, and the faint quote/background ornament was placed on the right testimonial side instead of the left title side.

Source measurements:

- Source Fatory `SLIDER-SPEC.md` records testimonial nav icons as `<i class='fa fa-angle-left'></i>` and `<i class='fa fa-angle-right'></i>`.
- Source CSS places the faint quote ornament on `.testimonial-items::after` with `left: 0`, `top: -15px`, `content: "\\f10d"`, `font-family: "Font Awesome 7 Free"`, `font-size: 100px`, and `opacity: 0.07`.
- Source browser inspection confirmed `.testimonial-box::after` has `content: none`; the quote ornament belongs to the left/title-side wrapper, not behind the right testimonial text.

Changes applied:

- Changed testimonial slider icons from `fa-solid fa-angle-left/right` to source-compatible `fa fa-angle-left/right`.
- Moved the faint quote ornament to `.testimonial-items-wrap::after`, matching the source left-side wrapper placement.
- Removed `.testimonial-box::after` so the quote no longer renders behind the right testimonial content.
- Extended `qa/lpf-source-design-contracts/factoria.json` to enforce testimonial quote placement, source icon classes, and forbid the old right-side quote pseudo-element.

Validation:

- Product `npm run build`: PASS.
- Product `npm run design:lint`: PASS with existing warning: `No YAML content found`.
- Root `npm run qa:lpf-memory-loop -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-testimonial-slider-icons-quote-placement.md`: PASS. STAMP MLP ticket=2026-06-30-lpf-repair-factoria-testimonial-slider-icons-quote-placement lane=LPF at=2026-06-30 digest=0b263cae.
- Root `npm run qa:lpf-dispatch-preflight -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-testimonial-slider-icons-quote-placement.md`: PASS. STAMP DPP ticket=2026-06-30-lpf-repair-factoria-testimonial-slider-icons-quote-placement lane=LPF at=2026-06-30 digest=ac7cdc11.
- Source-design contract: `LPF_REQUIRE_SOURCE_TYPOGRAPHY=1 LPF_LANDING_PAGE_SLUG=factoria python3 .../tools/check_lpf_conversion_contract.py --project-root .../factoria/repo --landing-page-slug factoria`: PASS.
- Local browser proof on `http://127.0.0.1:4376/`: PASS. Desktop and mobile testimonial controls use `fa fa-angle-left/right`, Font Awesome 7 Free renders the icons, `.testimonial-items-wrap::after` carries the visible quote glyph at `left: 0; top: -15px`, `.testimonial-box::after` is `content: none`, and next/previous controls changed active reviewer `Jones Adhor -> Mones Basel -> Jones Adhor`.
- Product commit `b55fe2e Repair Factoria testimonial controls` pushed to `origin/main`.
- Cloudflare production deployment `f6917d47-1900-4d7f-a283-c067d0efdb2f` from source `b55fe2e` published.
- Public browser proof on `https://factoria-landing-page.pages.dev/`: PASS. Quote pseudo-element remains on the left wrapper, old right-box quote is removed, controls use `fa fa-angle-left/right`, and next/previous controls changed active reviewer `Jones Adhor -> Mones Basel -> Jones Adhor`.
- Public root `npm run qa:lpf-rendered-output -- --url https://factoria-landing-page.pages.dev/ --output-dir qa/lpf-rendered-output/factoria-testimonial-icons-quote-public --expect-visible-text Factoria --forbid-placeholder`: PASS.
- Public root `npm run qa:lpf-funnel-sync -- --slug factoria ...`: PASS, MAE `5.82`, RMS `27.70`.

## Testimonial Slider Icon State Return

Owner returned Factoria again on 2026-06-30 because the testimonial slider icons still looked broken in the provided screenshot: the first-slide previous and next arrows both rendered as active black glyphs instead of showing the source finite-carousel boundary state.

Source facts:

- Source Fatory testimonial slider is finite (`loop: false` in the Owl config); it does not force rewind behavior for the testimonial carousel.
- Source Owl controls dim disabled boundary navigation through `.owl-theme .owl-nav .disabled { opacity: .5; cursor: default; }`.
- Source testimonial controls remain transparent, left-aligned, 24px Font Awesome angle icons with `fa fa-angle-left` and `fa fa-angle-right`.

Changes applied:

- Changed the testimonial Swiper configuration from `rewind: true` to `rewind: false` so Swiper applies boundary-disabled states.
- Added explicit testimonial disabled-state CSS for `.testimonial-prev.swiper-button-disabled` and `.testimonial-next.swiper-button-disabled`: `opacity: 0.5`, `cursor: default`, and `pointer-events: none`.
- Locked the testimonial icon glyphs to `Font Awesome 7 Free`, `24px`, and `900` weight so the source-compatible `fa fa-angle-left/right` classes render cleanly in the current Font Awesome package.
- Removed the stale mobile `.testimonial-box::after` override that remained after the quote ornament moved to `.testimonial-items-wrap::after`.
- Expanded `qa/lpf-source-design-contracts/factoria.json` so the self-improving loop checks the visible disabled-state styling and forbids the old testimonial rewind state.

Validation:

- Root `npm run factory:lpf:stopline`: PASS. Factoria remains a page rebuild candidate by total repair-ticket count, but no stopline threshold blocked this bounded testimonial repair.
- Root `npm run qa:lpf-memory-loop -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-testimonial-slider-icon-state.md`: PASS. STAMP MLP ticket=2026-06-30-lpf-repair-factoria-testimonial-slider-icon-state lane=LPF at=2026-06-30 digest=172a7d6a.
- Root `npm run qa:lpf-dispatch-preflight -- --ticket docs/factory-orders/2026-06-30-lpf-repair-factoria-testimonial-slider-icon-state.md`: PASS. STAMP DPP ticket=2026-06-30-lpf-repair-factoria-testimonial-slider-icon-state lane=LPF at=2026-06-30 digest=e466746a.
- Product `npm run build`: PASS.
- Product `npm run design:lint`: PASS with existing no-YAML warning.
- Product source-design contract: PASS.
- Local browser proof on `http://127.0.0.1:4381/`: PASS. Initial slide `Jones Adhor` shows `.testimonial-prev.swiper-button-disabled` at opacity `0.5` and active `.testimonial-next` at opacity `1`; clicking next changes to `Mones Basel` and disables the next control; clicking previous returns to `Jones Adhor`. Screenshot: `/tmp/factoria-testimonial-icon-state-local.png`.
- Product commit `9bf4a4c Repair Factoria testimonial icon state` pushed to `origin/main`.
- Cloudflare production deployment `011dbfff-ddbe-40be-9777-0ed03230ddee` from source `9bf4a4c` published.
- Public browser proof on `https://factoria-landing-page.pages.dev/`: PASS. Initial slide `Jones Adhor` shows `.testimonial-prev.swiper-button-disabled` at opacity `0.5` and active `.testimonial-next` at opacity `1`; `fa fa-angle-left/right` icons render with `Font Awesome 7 Free`, 24px, weight `900`; clicking next changes to `Mones Basel` and disables the next control; clicking previous returns to `Jones Adhor`. Screenshot: `/tmp/factoria-testimonial-icon-state-public.png`.

## Testimonial Slider Icon Clipping Return

Owner returned Factoria again on 2026-06-30 because the testimonial slider arrow icons were visible but their lower edge appeared chopped/overlapped at the bottom.

Root cause:

- Public geometry proof before repair showed `.testimonial-controls` still nested inside `.testimonials-carousel`, while `.testimonials-carousel` had `overflow: hidden`.
- The controls had `margin-bottom: -8px`; the arrow icon boxes extended 8px below the Swiper viewport, so the overflow-hidden carousel clipped the glyph bottoms.
- `.testimonial-box` also had `overflow: hidden`, which created a second possible clipping boundary around the controls.

Changes applied:

- Moved `.testimonial-controls` outside the `.swiper.testimonials-carousel` viewport while keeping them inside `.testimonial-box`.
- Removed the negative bottom margin from `.testimonial-controls` and set controls/buttons to `overflow: visible`.
- Set testimonial arrow buttons to a stable `24px` by `32px` box so 24px Font Awesome angle glyphs have vertical breathing room.
- Changed `.testimonial-box` overflow to `visible` so the testimonial module itself cannot crop the arrow controls.
- Expanded `qa/lpf-source-design-contracts/factoria.json` to enforce the safe controls location, zero bottom margin, visible overflow, stable button height, visible testimonial wrapper overflow, and to forbid the old negative-margin/hidden-wrapper clipping pattern.

Validation:

- Root `npm run factory:lpf:stopline`: PASS after acknowledging `factoria/testimonial-slider` as a repeated section-family escalation scheduled for holistic fidelity tracking.
- Product `npm run build`: PASS.
- Product `npm run design:lint`: PASS with existing no-YAML warning.
- Product source-design contract: PASS.
- Local browser proof on `http://127.0.0.1:4382/`: PASS. `.testimonial-controls` is no longer inside `.testimonials-carousel`; `.testimonial-box` overflow is `visible`; controls margin-bottom is `0px`; arrow buttons are `32px` high with visible overflow; glyph boxes sit fully inside the controls; no testimonial-module overflow-hidden ancestor contains the icons. Screenshot: `/tmp/factoria-testimonial-controls-after-local.png`.
- Product commit `a4c6df3 Repair Factoria testimonial icon clipping` pushed to `origin/main`.
- Cloudflare production deployment `bd60601e-c721-43f1-966e-38b0c359fcfb` from source `a4c6df3` published.
- Public browser proof on `https://factoria-landing-page.pages.dev/`: PASS. `.testimonial-controls` is not inside `.testimonials-carousel`; `.testimonial-box` overflow is `visible`; controls margin-bottom is `0px`; arrow buttons are `32px` high with visible overflow; Font Awesome angle glyphs render at 24px and sit fully inside the controls; no testimonial-module overflow-hidden ancestor contains the icons. Screenshot: `/tmp/factoria-testimonial-controls-after-public.png`.
