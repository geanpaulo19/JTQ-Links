# JTQ Global Support · Links

A single-page link hub for JTQ Global Support, built to the JTQ brand guide. No frameworks, no build step, no external dependencies. Everything is a local file.

---

## Preview

From this folder, run any static server:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

A server is recommended over double-clicking `index.html` because some browsers block locally loaded web fonts and the clipboard API when a page is opened from `file://`.

---

## What is in the box

```
index.html                  the whole page (HTML, CSS, JS inline)
site.webmanifest            install metadata for add-to-home-screen
assets/
  logos/
    jtq-logo-dark.svg       supplied logo, teal circle
    jtq-logo-light.svg      supplied logo, sand circle
  fonts/
    playfair-display-var.woff2
    playfair-display-italic-var.woff2
    montserrat-var.woff2
  photos/
    backdrop-flatlay.jpg    1600 x 900 page backdrop, pre-blurred and graded
  og-image.jpg              1200 x 630 social share card
  favicon.svg               browser tab icon
  apple-touch-icon.png      180 x 180 iOS home screen icon
  icon-512.png              manifest icon
  icon-square.svg           square icon source
preview/                    reference screenshots (safe to delete)
```

To deploy, upload `index.html`, `site.webmanifest` and the `assets/` folder. The original `JTQ Dark Circle.svg` and `JTQ Light Circle.svg` in the project root are the untouched source files and are not required by the page.

---

## The page

**A letterhead, not a template.** The page opens with a masthead: the JTQ mark and name on the left, a small "Links" label and the theme switch on the right, all sitting on a hairline rule. On phones the header spans the full content width, so the mark and the switch line up with the cards rather than floating in the centre. The page label steps out below 380px to keep the bar uncluttered. Below it, an italic eyebrow leads into an oversized Playfair headline, a short paragraph, and a closing line ("Everything is under control.") anchored above the locations and hours. On desktop the link stack sits opposite; on phones everything becomes one calm column.

The primary link is presented as a **ticket**: a deep teal card with an inset gold hairline, a gold globe seal and a large serif label. The four supporting links are quiet warm-white rows with gold hover accents and circular arrows. A faint vertical rule divides the two columns on wide screens.

Behind everything is a warm desk flatlay from Unsplash, pre-blurred and held at low opacity under the original sand, blush and sage gradients. It reads as warmth and texture rather than a photograph competing with the copy, and it is dimmed further in dark mode. The gradients themselves are unchanged.

**Links included**

| Label | Destination |
|---|---|
| Visit our website | https://jtq-global.com |
| Email us | mailto:hello@jtqglobal.com |
| LinkedIn | https://ph.linkedin.com/company/jtq-support |
| Instagram | https://www.instagram.com/jtqsupport |
| Facebook | https://www.facebook.com/profile.php?id=61584108250327 |

The website is treated as the primary destination (the teal ticket with a gold globe seal). The email row includes a **Copy** control so the address can be copied without opening a mail client. Copying shows a confirmation toast.

The footer carries the copyright on the left and the site credit on the right: **Site by Gean Paulo**, linked to geanpaulo.com.

**Light and dark.** The page follows the visitor's system theme on first visit, then remembers their choice. The switch sits at the right of the masthead. The supplied dark-circle logo is used on the light theme and the light-circle logo on the dark theme.

**Motion.** The headline rises in, the eyebrow fades up, the rows stagger upward, and the backdrop drifts in a very slow zoom. Cards lift and fill on hover, a gold line grows at the left edge, the ticket catches a soft pointer light, and the copy action confirms with a toast. All of it is disabled under `prefers-reduced-motion`.

---

## Brand tokens used

All values come from `JTQ Brand Guidelines.md`.

| Token | Value | Where |
|---|---|---|
| JTQ Teal | `#327075` | primary card, accents, links, dark-mode sparingly |
| Soft Sage | `#8FAFB0` | secondary washes, separators, focus accent in dark |
| Warm Sand | `#F4EFEA` | page background |
| Blush Nude | `#E7CFC9` | soft glow at the top right |
| Charcoal | `#2E2E2E` | text |
| Cloud White | `#FFFFFF` | link cards |
| Logo gold | `#FFD966` | logo, primary icon, small accents |

Type is **Playfair Display** for the headline, the ticket label and the closing motto, and **Montserrat** for everything else, exactly as the guide recommends.

Shape rule: the ticket uses a 22px radius, link rows 18px, icon tiles 14px, controls are full pills. Accent rule: teal is the interactive accent in light mode, sage in dark mode; gold is used for the brand mark, the ticket frame and small accents.

---

## Editing

Everything is in `index.html`, in the same order as the page.

- **Masthead:** the `masthead` block, including the logo link and the "Links" label.
- **Eyebrow:** `eyebrow` (the italic line above the headline).
- **Headline:** search for `brand__title`.
- **Intro paragraph:** `brand__lede`.
- **Closing motto:** `brand__motto`.
- **Locations and hours:** `brand__meta`.
- **A link:** duplicate a `.card` block and change the `href`, the `card__title`, the `card__sub` and the icon. Each `.card__icon` contains an inline SVG.
- **Group headings:** `group__label` (`Work with us`, `Follow along`).
- **Colours and type scale:** the `:root` block at the top of the CSS. Dark mode is the `[data-theme='dark']` block directly below it. The stylesheet has a base layer and a "v2 editorial layer" near the bottom; later rules win, so check both if a change does not appear.
- **Copy button:** the `data-copy` attribute on the button. Update it if the email address changes, and update the `mailto:` link above it.
- **Backdrop photograph:** replace `assets/photos/backdrop-flatlay.jpg` (a 16:9, softly blurred image works best). Tune its presence with `opacity` on `.ambient__photo`; tune the legibility scrim with `.ambient__veil`. Keep the gradients in `.ambient__wash` intact.
- **Site credit:** the footer `footer__credit` link. Point it wherever the developer credit should go.

Icons are from [Phosphor](https://phosphoricons.com) (UI icons) and [Simple Icons](https://simpleicons.org) (LinkedIn, Instagram, Facebook), inlined so the page has no external requests.

---

## Before you publish

1. **Set the absolute social image URL.** `og:image` and `twitter:image` currently point to `assets/og-image.jpg`. Most social platforms resolve that, but some require a full URL. Once the page has a home, replace both values with the absolute URL, for example `https://jtq-global.com/links/assets/og-image.jpg`, and add `og:url` plus a `<link rel="canonical">` with the final address.
2. **Check the links** in a private window on a phone. Instagram and LinkedIn sometimes redirect mobile users through an app prompt.
3. **Confirm the details** in the meta line: Dasmariñas, Philippines; Al Nahyan, UAE; daily 9am to 6pm PHT. These were taken from jtq-global.com.
4. **Optional:** add analytics (Fathom, Plausible, GA4) before `</body>`. The page ships with none.

---

## Accessibility and quality notes

- Colour contrast is at or above WCAG AA for all text. Normal-size text measures 5.2:1 or better across both themes; after the audit, the small labels over the dark photo measure 5.9:1 or better (most are 7:1+). The italic headline word is 4.4:1 in light (large text only needs 3:1) and 9.8:1 in dark.
- Dark-mode hover uses a raised charcoal surface instead of white. Hovered social text measures 6.4:1 or better, and the page no longer flips to an unreadable light card.
- Audited with axe-core 4.10.2 against WCAG 2.2 AA at 1440 and 320 in both themes, including a hovered card: **0 violations**. Axe reports 25 contrast checks as "incomplete" because the page sits on a photograph; each was sampled against the rendered pixels and passes.
- Fully keyboard navigable with 2px focus rings that stay visible on the ticket, the rows, the copy control and the theme switch. Tab order: masthead link, theme switch, website, email, copy, socials, site credit.
- The theme switch is a real `role="switch"` with `aria-checked`. The copy control's live region starts empty and announces only after a copy.
- External links carry an off-screen "opens in a new tab" note for screen readers. Decorative artwork and icons are `aria-hidden`; every link has visible text.
- Touch targets are 36px or larger (AA minimum is 24px): rows 76-84px, copy 36px, theme switch 40px.
- Motion respects `prefers-reduced-motion`.
- The page itself loads roughly 240 KB (HTML, three self-hosted fonts, the logos and one 48 KB backdrop) with no external requests. The social card (133 KB) is only fetched by link previews. Fonts are preloaded.
- Responsive from 320px up; tested at 320, 390, 768, 1024, 1280 and 1440.

---

## Credits

Design and build by [Gean Paulo](https://geanpaulo.com).

Playfair Display and Montserrat are licensed under the SIL Open Font License 1.1, self-hosted from Google Fonts. Phosphor icons are MIT. Simple Icons brand marks are CC0 1.0.

Photographs are from [Unsplash](https://unsplash.com) and used under the [Unsplash License](https://unsplash.com/license): the page backdrop is a desk flatlay, and the social card uses a quiet desk scene. Both are self-hosted and colour-graded, never hotlinked. Photography does not have to carry a credit under that licence, but keep this note if images are ever swapped.

The JTQ logos and brand palette remain the property of JTQ Global Support.
