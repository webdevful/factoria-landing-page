# Forge Line Design Contract

## Source Baseline

- Source URL: `https://validthemes.net/site-template/fatory/?storefront=envato-elements`
- Capture: `/Volumes/WDF-NAS-01/04-Projects/Internal-Projects/Codebases/webdevful-astro-main/captures/validthemes-net-site-template-fatory/desktop/screenshot-fullpage.png`
- Structure: one-page industrial template with hero slider, about block, service grid, work process row, project slider, team, testimonials, blog, partner logos, and dark footer.
- Runtime: final implementation uses Swiper carousels and smooth scroll-to-top.

## Tokens

```json
{
  "color": {
    "ink": "#232323",
    "inkSoft": "#555555",
    "paper": "#ffffff",
    "paperSoft": "#f7f7f7",
    "white": "#ffffff",
    "muted": "#777777",
    "line": "#e5e5e5",
    "yellow": "#ffb606",
    "yellowDark": "#e09f00",
    "darkBg": "#1d2024",
    "darkBgSoft": "#25282d"
  },
  "typography": {
    "display": "Outfit, Inter, system-ui, sans-serif",
    "body": "Inter, system-ui, sans-serif",
    "heroDesktop": "clamp(3.5rem, 8vw, 7.5rem)",
    "sectionTitle": "clamp(2.0rem, 4.5vw, 4.0rem)",
    "bodyLineHeight": "1.7"
  },
  "shape": {
    "radius": "0px",
    "logoStripMark": "83px",
    "scrollTop": "50px",
    "desktopContainerX": "clamp(15px, 5vw, 80px)"
  }
}
```

## LPF Adaptation Notes

- WLFS generated the header/footer logo and favicon assets.
- Photographic slots use local downloaded Unsplash JPEG replacements.
- Sponsor strip uses approved text-only placeholders preserving circular source logo geometry.
- No source template logo assets are shipped in the product repo.
