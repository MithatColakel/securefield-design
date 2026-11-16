SecureField is a VPN app for iPhone, iPad and Mac, used mainly in the Middle East and North Africa. Every screen is dark: a graphite-to-black page, a faint world map, light text, one green action. Build new screens from the tokens and components here. Copy values exactly; do not round them.

## Content

- Write short and plain. One idea per line. Titles are a few words: "Surf the Web Privately", "Fast & Stable Connection", "How was your connection?".
- Speak to the user as "you" and of the company as "we": "We ended the session — nothing went wrong. How was it while it lasted?".
- Use Title Case for screen titles and offers ("Get Premium Now", "Access Global Content"). Use sentence case for status, body text and errors ("Tap to connect", "Connection failed. Please try again").
- Status words are one or two words: "Connected" / «متصل», "Connecting" / «جارٍ الاتصال», "Disconnecting", "Analyzing network".
- Name the product "Securefield VPN" in text (lower-case f). The protocol "Securefield Shield" and the names OpenVPN, Wireguard, Hysteria2 and App Store stay in Latin script in Arabic.
- Upper-case only short labels: the add-time pill ("ADD"), "RECOMMENDED", the iPad "PREMIUM" header. Upper-casing does nothing to Arabic.
- No emoji. No exclamation marks, except the last onboarding title "Connect now!".
- Every string ships in English and Arabic. Write the Arabic as its own text, not a word-for-word copy: "Get Premium" is «احصل على المميز», "Not now" is «ليس الآن».

## Colour

- There is one theme, `dark`. The app pins it. Do not add a light theme.
- Page: `gradient-background` (`bgGraphit` → `bgBlack`, top-leading to bottom-trailing), with `assets/Images/World-Map.png` in overlay blend. Mac windows use the same gradient; the Mac paywall uses `gradient-macPaywall`.
- Cards on iPhone and iPad: `background-secondary` (`iceBlue`, 20 %) with the 1 pt `gradient-border`. Mac cards: `surface` with a 1 pt `hairline`.
- Sheets on iPad and Mac: `sheetBackground`. Pop-ups dim the page with `background-quaternary`.
- Text: `text-primary` (white) for titles and body. `text-tertiary` (`lightGray`) for hints and secondary lines. `text-secondary` (`lightGreen`) for success and links: "Connected", "Change", "Restore", legal links. `text-quaternary` (`lightYellow`) only for premium. `text-error` (`lightRed`) only for errors and the Auto-row signal bars.
- Green means "go" and "connected". Yellow means premium. Do not use yellow for warnings; the discouraged protocol uses `discouraged`.
- The main action is `RadialGradientButton` (green, `gradient-controlGreen`). Use one per screen. On the Mac it is `MacButtons` Primary (`gradient-macPrimary`). Premium on the Mac is `gradient-premium` with `onPremium` text.
- Literal colours with no token in code are tokens here with "Literal" in their note (`splashFill`, `loadingTint`, `onPremium` …). Use them only where their note says.

## Type

- Headings and button labels: NAMU-1850 (`H4`, `H5`, `H6`, `Subtitle1`; Mac `display`, `title`, `headline`, `subtitle`). The font file is `fonts/NAMU-1850.ttf`, copied from the app. It has one weight (400). It has no Arabic glyphs.
- Body: Red Hat Display (`Body1`, `Body2`, `Caption`, `Amiko3`, `Amiko4`; Mac `body`, `bodyBold`, `caption`). The add-time pill uses Amiko (`Amiko2`).
- Mac timers and shortcut keys: `mono` (system monospaced).
- On iPad (shortest side 600 pt or more) every iPhone size and line height is × 1.3. The Mac styles do not scale.
- Arabic text uses the system Arabic font. The brand fonts have no Arabic glyphs. Keep the same size and weight.

## Layout and spacing

- iPhone and iPad sizes are fractions of the layout width, not fixed points: the large button is `0.83 × width` by `width / 4.64`. Each component guideline gives its fractions. Keep the fraction; do not convert it to a fixed size.
- The iPad uses a server column (400 max) beside the main column, and form sheets (Settings 1000 × 720, Report 540 wide).
- Mac spacing is `space-xs` … `space-xxl` and `space-page`. The main window is 920 × 620 (min 820 × 560) with a 320 sidebar; the menu bar panel is 340 wide; Settings is 460 × 700.

## Radii, borders, shadows

- Cards: `radius-gradientCard` (28). Buttons: `radius-button` (24). Fields and notice bands: `radius-field` (12). Mac: `radius-chip`, `radius-card`, `radius-panel`.
- Borders are 1 pt. Cards use `gradient-border`; pills and tags use `border-quaternary`; buttons add white 10 % inside.
- Cards and radios have a 1 pt inner `highlight` stroke. There is one real shadow: `shadow-grabber`. Do not add drop shadows.

## Imagery and motion

- The world map (`World-Map.png`) is the only background image, except the Advertisement top (`Advertisement-Background.png`).
- Motion is Lottie: the Connect button (`TTC`, `TTD`), onboarding (`Lock`, `Globe-and-pins`, `Speedometer`, `Shield`) and splash (`Logo`). Use the files in `assets/Lotties/`; do not redraw them.
- Buttons press to scale 0.97 and `opacity-pressed` with a short spring. The Mac connect orb breathes (1 → 1.12, 2.4 s) only while connected.

## States

- Pressed: `opacity-pressed` (Connect: `opacity-connectPressed`). Disabled: `opacity-disabled` (Mac: `opacity-disabledMac`). Loading: the system spinner; on the paywall, `loadingTint` in a `loadingBox`.
- Selected rows and radios: green (`gradient-green`, `background-tertiary` at 16 % on iPad). The chosen paywall plan: `gradient-controlOrange` border.

## Iconography

- iPhone and iPad use the app's own icons in `assets/Icons/`. Most keep their own ink (see the group README). Flags are `assets/Flags/<CODE>.svg`, with `EARTH.svg` when no flag exists.
- The Mac uses SF Symbols (`crown.fill`, `chevron.forward`, `gearshape` …). They are not in the repo; previews draw stand-ins. Some iPhone glyphs are SF Symbols too (`xmark`, `magnifyingglass`); each component says which.
- Logos: `assets/Logos/App-Logo.png` in headers, `Splash.png`, `Privacy-Logo.png`, the premium crown `Premium.png`, and the app icons. Never redraw a logo.

## Arabic and right-to-left

- Every screen mirrors in Arabic: leading and trailing swap, rows read right to left, the back and row chevrons turn.
- Flags, the logo and the Connect button do not mirror. The page gradient's diagonal mirrors (top-right start): the whole UI follows the locale.
- Timers (`HH:MM:SS`) stay in Latin digits, left to right inside the line. Long dates use Arabic-Indic digits. Prices come formatted from the App Store.
- Arabic lines are often longer. Allow them to wrap; do not cut them.
- The whole UI follows the locale. Left-to-right is forced only on the connect button, some Mac panel and main-window rows (for example the timer), the Design connect and settings rows, and one wide-layout container. Arrows mirror in Settings, Document, the wide layout and the server-list back icon. Mirroring that no screenshot shows yet is marked "to confirm" in the component guideline.

## Contrast

Measured with WCAG 2 on the lightest point of each ground (the worst case for light text). Text needs 4.5:1 (3:1 at 24 px or more, or bold 19 px or more). Icons, borders and marks that carry meaning need 3:1.

These pairs pass:

| Foreground | Ground | Ratio | Where |
|---|---|---|---|
| `text-primary` #FFFFFF | page #172231 | 16.04 | body, titles, server names |
| `text-primary` | card #2C3F58 | 10.72 | text on GradientBorderCard |
| `text-tertiary` #D1DCEA | page / card | 11.56 / 7.72 | hints, header and back icons |
| `text-tertiary` | iPad sheet card #25354B | 8.92 | Settings sheet |
| `text-secondary` #35DF91 | page / card | 9.25 / 6.18 | Connected, Change, links |
| `text-secondary` | Recommended tag #2D525E | 4.87 | "RECOMMENDED", Red Hat Bold 10 |
| `text-quaternary` #FAC762 | page / card | 10.24 / 6.84 | premium lines |
| `text-error` #F47960 | page | 5.92 | errors |
| `text-error` (marks) | card | 3.96 | Auto-row signal bars |
| `bgGraphit` #172231 | `gradient-radialOrange` | 6.74–10.24 | PremiumMark |
| `onPremium` #1B1305 | `gradient-premium` | 7.73–11.74 | Mac premium button, Badge |
| `lightGray` #D1DCEA | Mac `surface` #252F3D | 9.72 | Mac cards, search field |
| `mediumGray` #8C9197 | Mac page / sheet | 5.05 / 5.72 | Mac captions, list headers, fine print |
| `auroMetalGray` #6D767D | Mac page | 3.47 | Mac idle timer (34 / 30 semibold: large text) |
| `lightGreen` / `lightGray` | Mac paywall top #0F3A4D | 6.99 / 8.74 | Mac paywall |
| `loadingTint` #5AAD79 | `loadingBox` #3A3F46 | 3.88 | paywall spinner |

These pairs fail. They are kept exactly as the app has them. Do not copy them into new designs until a fix is approved:

| Foreground | Ground | Ratio | Need | Where | Proposed fix (not approved) |
|---|---|---|---|---|---|
| `text-primary` #FFFFFF | `gradient-controlGreen` at the label centre #2ABF7A (lightest #35DF91) | 2.37 (1.73) | 4.5 | RadialGradientButton label, NAMU 17 | Label in `bgGraphit`: 6.76 (9.25 at the lightest point). Or keep white and darken the ground under the label to #1E8756: 4.51. |
| `text-primary` | same, Report "No problem to report" #2CC67F | 2.22 | 4.5 | fill(56/18), NAMU 15 | Same as above. |
| `text-primary` | `gradient-controlTagBlue` at the label #2CA2F6 | 2.77 | 4.5 | PremiumCardTag, Red Hat 12 | Label in `bgGraphit`: 5.80. Or darken to #227CBC: 4.51. |
| `text-primary` | `gradient-macPrimary` #33A9FE → #1EB972 | 2.55–2.60 | 4.5 | Mac Primary button and panel Connect, `bodyBold` 15 | Label in `bgGraphit`: 6.29–6.30. Or darken the stops to #257CBA → #168854: 4.51. |
| `icon-secondary` #3F4751 | FeedbackSheet card #19222F | 1.70 | 3 | FeedbackSheet close icon (template) | `icon-primary` #D1DCEA, as the other close icons: 11.52. Smallest change: #656C74, 3.00. |
| `paginator-primary` #3F4751 | page #172231 | 1.70 | 3 | inactive onboarding dot | `auroMetalGray` #6D767D: 3.47. Smallest change: #656C74, 3.00. |
| `discouraged` #E5484D | card #2C3F58 | 2.74 | 3 | protocol row "!" and its border | `text-error` #F47960: 3.96. Smallest change: #E7565B, 3.00. |

Not measured, because the system draws the ground: macOS grouped forms, title bars and list selection; the iOS `ultraThinMaterial` under the FeedbackSheet card (the ratio above leaves it out); the world map, which lightens the page a little in places. `separator-secondary` and the splash track are decorative and need no ratio.

## Screens

Every screen of the app is on the app's screen canvas (Claude Design).
