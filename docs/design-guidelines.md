# Sii website design reference

Extracted from [sii.pl](https://sii.pl/) on 2026-10-17 using Playwright CLI in **visible Google Chrome**, desktop viewport 1440 × 1000. This is an observed homepage reference, not an official brand manual. Cookie consent was dismissed using “Odrzuć wszystkie pliki cookies”; the full-page screenshot was visually checked for overlays after scrolling to load images. The hero is a rotating carousel, so its slide can change between measurements and screenshots.

## Assets

| Asset | Local file |
| --- | --- |
| Full homepage screenshot | [homepage.png](../assets/homepage.png) |
| Structured tokens | [design-tokens.json](../assets/design-tokens.json) |
| Original Sii wordmark | [logo.svg](../assets/logo.svg) |
| 32 × 32 favicon | [favicon.png](../assets/favicon.png) |

The original wordmark was fetched from `https://sii.pl/wp-content/themes/sii-sage/resources/assets/images/logo-sii-svg.svg`. The favicon came from `https://sii.pl/wp-content/uploads/2020/03/cropped-logo-sii-icon-1-32x32.png`. No hero photography, client logos or background imagery was downloaded separately.

## Colors

| Token | Value | Observed usage |
| --- | --- | --- |
| brand.primary | #0E6EE0 | Links, contact border, gradient midpoint |
| brand.purple | #4C38C6 | Brand gradient start |
| brand.accent | #47DDE2 | Brand gradient end, highlighted text |
| brand.mint | #73FFC3 | Alternate AI gradient end |
| background.default | #FFFFFF | Main content sections |
| background.light | #F5F9FE | Light surfaces and contact CTA |
| text.primary | #2B2B2B | Body text and headings; newsletter button fill |
| text.secondary | #7F7F7F | Secondary text and newsletter border |
| text.muted | #B7B7B7 | Low-emphasis text; not a default body color |
| text.onDark | #FFFFFF | Hero text and navigation |
| text.outlineButton | #2079E2 | “Więcej” outline button |

Brand gradient: `linear-gradient(95deg, #4c38c6, #0e6ee0 50%, #47dde2)`. Alternate AI gradient: `linear-gradient(95deg, #0e6ee0, #47dde2 50%, #73ffc3)`. Gradient text uses background clipping; its computed black text color is not its visible appearance. The hero dark blue/purple treatment comes partly from imagery, so a flat fill cannot reproduce it. A case-study overlay uses `linear-gradient(0deg, #020024, rgba(255,255,255,0.396))`.

Error and success colors were not observed and are `null` in the tokens. Do not infer validation colors from the decorative palette. Check contrast for the intended text size and background before adapting the reference.

## Typography

Use `Lato, sans-serif`. The source provides self-hosted subset fonts via `https://sii.pl/wp-content/themes/sii-sage/resources/fonts/fonts.css`; all seven WOFF2 files were downloaded from that same origin.

| Face | Repository path |
| --- | --- |
| Bold | [`assets/fonts/lato/subset-Lato-Bold.woff2`](../assets/fonts/lato/subset-Lato-Bold.woff2) |
| Heavy | [`assets/fonts/lato/subset-Lato-Heavy.woff2`](../assets/fonts/lato/subset-Lato-Heavy.woff2) |
| Light | [`assets/fonts/lato/subset-Lato-Light.woff2`](../assets/fonts/lato/subset-Lato-Light.woff2) |
| LightItalic | [`assets/fonts/lato/subset-Lato-LightItalic.woff2`](../assets/fonts/lato/subset-Lato-LightItalic.woff2) |
| Medium | [`assets/fonts/lato/subset-Lato-Medium.woff2`](../assets/fonts/lato/subset-Lato-Medium.woff2) |
| Regular | [`assets/fonts/lato/subset-Lato-Regular.woff2`](../assets/fonts/lato/subset-Lato-Regular.woff2) |
| Semibold | [`assets/fonts/lato/subset-Lato-Semibold.woff2`](../assets/fonts/lato/subset-Lato-Semibold.woff2) |

Map Light to 300, Regular to 400, Medium to 500, Semibold to 600, Bold to 700 and Heavy to 900. LightItalic uses weight 300 and `font-style: italic`; all other faces use normal style. Verify the font licenses before using or redistributing these local files; glyph coverage of the source subsets has not been audited.

```css
/* Example when served from /assets; adjust URLs to the application's asset pipeline. */
@font-face {
  font-family: 'Lato';
  src: url('/assets/fonts/lato/subset-Lato-Regular.woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

Register each required weight with its own file; do not use the regular file for every weight.

| Role | Font size / line height | Weight |
| --- | --- | --- |
| Fine print | 12px / context dependent | 400 |
| Supporting text | 14px / context dependent | 400 |
| Base / navigation | 16px / nav 19px | 400 / nav 600 |
| Standard button | 17px / 19px | 400 |
| Hero teaser | 18px / 28px | 400 |
| Content / card sizes | 22px, 28px | Context dependent |
| Section heading | 45px / 55px | 400 |
| Key statistics | 55px / 66px | 400 |
| Desktop hero | 145px / 145px | 900 |

Uppercase section labels and a heavy, two-line hero establish hierarchy. These are desktop measurements; mobile sizes and breakpoints were not extracted. Avoid applying the 145px hero size globally.

## Spacing and layout

A 4px base with 4, 8, 12, 16, 20, 24, 28 and 32px is a **proposed implementation scale**, not an asserted source token system. Measured components also use 5, 9, 10, 25, 29, 30 and 33px. Preserve measured values when matching an existing component.

The centered desktop content/header container is 1140px at a 1440px viewport, leaving approximately 150px side margins. Section spacing is generous: 40, 60, 100, 120 and 160px occur. The “Dlaczego my” section uses `160px 0 100px`; the news section uses `160px 0 120px`. Keep this spacious rhythm for marketing pages, then define app-specific density separately.

## Border radii

| Value | Context |
| --- | --- |
| 0px | Text, navigation, many structural surfaces |
| 4px | Small UI details |
| 5px | Language selector |
| 8px | Rounded surfaces/details; some corners only |
| 20px | Standard and compact pill buttons |
| 42px | Larger pill controls |
| 50% | Circular indicators |
| 35px 0 0 35px | Newsletter input left corners |

Some source surfaces use `0 0 8px 8px` or `8px 0 0 8px`; do not round every corner indiscriminately. Values outside the directly described components are observed occurrences, not semantic assignments from an official system.

## Components

- **Header:** transparent over the dark hero; centered 1140px desktop container, measured overall height 182px. Logo is approximately 102 × 66px at the upper left. Utility links sit above the main navigation.
- **Navigation:** white Lato 16px/19px, weight 600, `10px 12px` item padding. Dropdown arrows accompany expandable groups. Mobile navigation behavior and hover/focus styling were not characterized.
- **Primary compact CTA (“Dołącz do nas”):** brand gradient, white text, 16px/18px regular, `5px 20px` padding, 30px height, 20px radius, no border.
- **Secondary compact CTA (“Kontakt”):** #F5F9FE background, #0E6EE0 text and 1px border, otherwise the same compact dimensions.
- **Outline CTA (“Więcej”):** transparent fill, #2079E2 text and 1px border, 17px/19px, `9px 33px 8px` padding, 38px height and 20px radius. On dark photography, use the observed white text/border variant.
- **Text CTA:** #0E6EE0, 17px/19px regular, no background or border. Several cards use “Zobacz więcej”.
- **Cards and sections:** photography-led cards, restrained text, blue links, light surfaces and substantial whitespace. Technology/client logo grids provide a consistent alignment rhythm.
- **Newsletter input:** white fill, #7F7F7F text and 1px border, 14px/14px, `9px 100px 10px 21px` padding, 38px height, `35px 0 0 35px` radius. Its dark #2B2B2B “Subskrybuj” button has white 17px/19px text, `10px 22px` padding and 20px radius. No form was submitted.
- **Footer:** blue/purple image/gradient treatment, white supporting text, newsletter and social links. No separate promotional bar was confirmed.

## Logo usage

Use the original SVG as supplied, preserving its aspect ratio and internal colors. The screenshot shows the supplied mark on a dark hero background; verify its legibility in the actual placement. No separate inverted logo was confirmed or generated. No official minimum size or clear-space rule was discovered; give it ample space and do not invent such rules as brand requirements. Logos, fonts and screenshot imagery may be protected: verify usage and redistribution rights before product use.

## Visual style summary

The site combines a corporate technology presentation with energetic blue, purple and cyan gradients. Large heavy hero type contrasts with lighter section headings and calm body text. Photography of people and projects gives the page a human focus. Rounded CTAs, expansive white sections and aligned logo grids keep the dense marketing content structured.

## Verification and limits

The live page loaded successfully in headed Chrome; consent buttons disappeared after dismissal. The full-page PNG was opened and checked visually with no consent/modal overlay. Font downloads completed with seven valid WOFF2 files and one PNG favicon; the logo contains valid SVG markup. This task creates reference assets and documentation only; no application runtime was changed. The source site's console logged repeated `showMoreByHeight` missing-element messages during lazy loading; these originate from the external site. Responsive rules, interaction states, full accessibility behavior and semantic form validation remain unverified.
