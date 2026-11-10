# LSH Design System — v2 (Approved Direction)

Light, warm, editorial. Reference category: modern DTC telehealth (forhers.com / ro.com energy) — **not** dark corporate, **not** generic teal-medical. v1 (dark navy backgrounds, stacked card grids) was rejected; do not regress.

## Color tokens

| Token | Hex | Use |
|---|---|---|
| `--paper` | `#FBF9F5` | Page background (warm off-white) |
| `--sand` | `#F3EDE3` | Soft section tint, footer, family bar |
| `--shell` | `#EFE6D8` | Deeper warm tint (big CTA block) |
| `--navy` | `#12134B` | **Brand ink.** Headings, logo, primary buttons. Never a full-bleed page background. |
| `--ink` | `#1E2040` | Body headings/text |
| `--soft` | `#5A5C78` | Secondary text |
| `--apricot` | `#E7A576` | Highlights, flags, step numerals |
| `--apricot-deep` | `#D98D57` | CTA hover, eyebrow labels, links |
| `--sage` / `--sage-tint` | `#B4C4AE` / `#EAF0E6` | Life Solution Labs accent only |
| `--blush` | `#F4E3D3` | Check-icon chips, warm photo gradients |
| `--line` | `#E7E0D3` | Borders, dividers |

## Typography

- **Display:** Fraunces, weight 400–500, tight leading (1.08), slight negative tracking. Italic for emphasis words and pull quotes.
- **UI/body:** Figtree 400–700.
- Scale: h1 `clamp(40px, 5.4vw, 64px)` · h2 `clamp(30px, 3.6vw, 44px)` · body 16.5px · lead 19px.
- Eyebrow labels: 12.5px, 700, letter-spacing .16em, uppercase, apricot-deep.

## Signature shapes

- **Arch photo frame:** `border-radius: 200px 200px 28px 28px` — the visual signature; use on all hero/feature imagery.
- **Pill buttons:** `border-radius: 999px`; navy fill → apricot-deep hover (+1px lift). Ghost variant: navy border, fills on hover.
- Cards/panels: 28px radius; spotlight panels 40px.

## Section rhythm (homepage canon)

Alternate shapes and densities — never three same-pattern sections in a row:

`hero (text + arch photo)` → `trust strip (4 claims)` → `3 photo tiles` → `editorial split (photo + checklist)` → `4 numbered steps (white band)` → `provider spotlight (sand panel, pull quote)` → `3 testimonial cards` → `FAQ accordion` → `big CTA (shell panel)` → `footer (sand)`

## Voice

Short, confident, benefit-first, warm. One primary CTA repeated verbatim everywhere: **"Am I eligible?"**
Examples of register: "Weight loss that starts with *your* biology." · "Most platforms sell you medication. We practice medicine." · "One number. That's the whole trick."

## Sister-brand treatment

- Slim light "family bar" above nav (sand bg, pill active state) — never a heavy dark band.
- Dr. Clisby pages: blush/apricot palette. Labs pages: sage palette. Everything else: core palette.

## Accessibility & responsive

- WCAG AA contrast minimum (navy on paper passes everywhere; verify apricot text usage stays ≥ 4.5:1 for body sizes).
- Mobile-first at 380px; 16–28px gutters; no horizontal scroll; grids collapse to single column ≤ 900px.
