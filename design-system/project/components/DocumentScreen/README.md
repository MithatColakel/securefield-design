# DocumentScreen

The legal and help documents on iPhone and iPad, and the FAQ list that opens them. A document is a bundled HTML page in a web view, under `LargeTitleBar`.

Source: `UI/DocumentScreen.swift` (`DocumentScreen`, `DocumentSheet`, `FAQScreen`). Pages: `Resources/Documents/<name>[.<language>].html`.

## Documents
| ID | Title key | English title | Reached from |
|---|---|---|---|
| `payment` | `DOCUMENT.PAYMENT` | Payment & Subscription | FAQ |
| `cant-connect` | `DOCUMENT.CANT_CONNECT` | Can’t connect | FAQ |
| `cant-access` | `DOCUMENT.CANT_ACCESS` | Can’t access Web/App | FAQ |
| `profile` | `DOCUMENT.PROFILE` | Profile/Installation | FAQ |
| `how-works` | `DOCUMENT.HOW_WORKS` | How Securefield works? | FAQ |
| `other` | `DOCUMENT.OTHER` | Other Issues | FAQ |
| `privacy` | `DOCUMENT.PRIVACY` | Privacy Policy | Settings, legal footers |
| `terms` | `DOCUMENT.TERMS` | Terms of Use | Settings, legal footers |
| `about` | `DOCUMENT.ABOUT` | About Subscription | legal footers |

Arabic pages on main: `about`, `cant-connect`, `other`, `privacy`, `terms`. The other four show the English page in Arabic.

## DocumentScreen layout
- Ground: `GradientBackground`. The web view is transparent and runs edge to edge, from the top of the screen (under the bar) to the bottom (under the home indicator).
- Bar: `LargeTitleBar` with the document title. Back (`chevron.backward`) when pushed from Settings or the FAQ. Close (`xmark`) when opened in a sheet from a legal footer (`DocumentSheet`).
- Page type comes from each page's own stylesheet, not from tokens: Red Hat Display Regular 16 px, white `#fff`, links without underline. Headings (`h3`, `h4`, `b`) use the web view's default sizes and bold.
- The app adds side margins of 20 to the page body. The web view's default top and bottom body margin (8) stays.
- Space under the last line: 100 (`contentInset.bottom`).
- Links to `http`, `https` and `mailto` open outside the app.
- Arabic and Hebrew pages set `dir="rtl"` themselves. The web view takes the direction from the page, not from the app.

## FAQScreen layout
- Ground: `GradientBackground`. Bar: `LargeTitleBar` "FAQ" (`FREQUENTLY_ASKED_QUESTIONS.HEADER.TITLE`).
- One `GradientBorderCard` (radius 28), width `layoutWidth × 0.915` (356.9 at lw 390), centred, padding 16 above and below. It scrolls, so the title can fold.
- Six rows, height 64, padding sides 20: title `Body1` leading, flexible space (min 8), `assets/Icons/Next.svg` 24 × 24 tinted `--icon-primary`. A `RowSeparator` between rows.
- Pressed: a plain button (no press style).

## Right-to-left
- FAQ: titles right-aligned. `Next` mirrors (`flipsForRightToLeftLayoutDirection(true)`) and points left. The separators start from the right.
- Documents: the Arabic page is right to left by its own `dir`. Latin words inside (Securefield VPN) keep normal bidi order.

## States
One state per page. A missing page file shows its ID in white system text (a build fault, not a designed state).

## Notes
- **Vertical positions to confirm.** The preview starts the page under a stand-in bar (see LargeTitleBar). The positions are checked against device screenshots.
- The preview shows the first lines of `cant-connect.html` and `cant-connect.ar.html` as they are on main, with their stylesheet. The page's `Red Hat Display` loads from `fonts/`.
- Two Arabic pages on main are damaged (`privacy.ar.html`, `terms.ar.html`), and `cant-connect.ar.html` has small markup faults: the loose "-" lines and the stray "I" in the Arabic preview are in the shipped file. They are kept as shipped.
