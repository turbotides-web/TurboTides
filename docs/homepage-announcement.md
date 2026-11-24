# Homepage Hero Announcement Panel (high-prominence design)

Status: implemented Nov 24, 2026, uncommitted at time of writing. Approved direction from the CEO: the Nov 20, 2026 jury verdict statement must be "impossible to overlook" during the announcement period. This file records the design so it can be restored, tuned, or retired deliberately.

## Where it lives

- Markup + CSS: `layouts/shortcodes/video-hero.html` (anchor `.hero-news-card`, CSS in the `<style>` block marked "HIGH-PROMINENCE ANNOUNCEMENT PANEL").
- Content: `content/_index.md`, `news[0]` (`title`, `link`, `label`). Only `news[0]` is shown. Link text "Read the Full Statement →" is fixed in the shortcode.
- Target article (do not edit for styling): `content/blog/news/jury-verdict-statement/index.md`.
- Hero headline position/scroll indicator are in `assets/css/home.css` (`.hero-headlines`, `.hero-scroll-indicator`); not changed by this work.

## Design spec (keep unless the CEO/owner asks otherwise)

Desktop (>768px):
- Whole panel is one `<a>` (no nested links). Centered, `bottom: 80px`, `width: min(900px, 100% - 3rem)`, square corners.
- Background TurboTides brand blue `#004292` at 80% opacity (`rgba(0,66,146,.8)`; owner-chosen over solid charcoal `#151f29`, solid blue and pale `#EAF4FB` variants), 1px border `rgba(255,255,255,.22)`; no gradient, blur, shadow, or icon. Owner first asked for "70%", then raised it to 80%; read as opacity, since white text would fail contrast at 30% opacity.
- Padding `2.5rem 3rem 2.25rem`, gap 1rem.
- Label: 13px (.8125rem), 600, uppercase, letter-spacing .16em, `rgba(255,255,255,.9)`. The label text in content is title case; CSS uppercases it to "OFFICIAL STATEMENT · NOVEMBER 20, 2026".
- Headline: 34px (2.125rem), 700, line-height 1.22, white, `text-wrap: balance`.
- CTA: 15px, 600, underlined with a 1px bottom border; arrow nudges 4px on hover/focus.
- Hover/focus: background opacity rises to .9, border brightens; focus-visible adds 3px white outline, 4px offset. No pulsing or looping animation.

Mobile (<=768px): `bottom: 56px`, `width: calc(100% - 2rem)`, padding `1.25rem 1.25rem 1.1rem`, label 11px, headline 22px, CTA 13px.

The scroll indicator was removed from the hero at the owner's request (its CSS remains, unused, in `assets/css/home.css`), so the panel sits lower. Verify positions by rendering at 1440x900 and 390x844.

## Previous design (for rollback)

Small centered translucent card: `bottom: 18%`, `width: min(580px, 100% - 2rem)`, padding `.95rem 1.5rem 1.05rem`, `background: rgba(40,52,58,.6)` with `backdrop-filter: blur(6px)`, label .75rem, title 1.12rem/600, no CTA line. It is in git history (commit `faaf1b0`, `layouts/shortcodes/video-hero.html`). A scaled-down intermediate (e.g. 90-95% opaque panel, smaller headline) is the intended path if the CEO wants less prominence; change values in the one CSS block rather than redesigning.

## Constraints to preserve

- Do not re-add a news strip (`home-news`) below the hero.
- Do not change the approved statement's wording or `assets/css/news.css` styling for this feature.
- `video-hero.html` contains legacy GBK comment bytes: edit byte-safely (e.g. Python read/write bytes as latin-1), not with encoding-converting tools. It is CRLF.
- Panel must stay fully visible at 1440x900 and 390x844 without scrolling and must not overlap the scroll indicator.

## How to retire after the announcement period

Replace `news[0]` in `content/_index.md` with the next item (drop `label` to hide the eyebrow) and, if a small card is wanted again, restore the previous CSS from `faaf1b0`. The article itself stays permanently.
