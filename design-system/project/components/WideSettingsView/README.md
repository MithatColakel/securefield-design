# WideSettingsView

Settings on iPad in a wide window: a form sheet with the sections in a sidebar on the left and the chosen section on the right, as in the iPadOS Settings app.

Source: `UI/WideLayout.swift` (`WideSettingsView`, `FormSheetWhenWide`, `WideFormSizing`, `WideLayout`).

## When it shows
- The window is at least `WideLayout.twoColumnMinWidth` 700 wide. Narrower, the iPhone Settings screen is pushed as on the phone.
- `FormSheetWhenWide` makes Report a form sheet (`.presentationSizing(.form)`) in a wide window. In a narrow window nothing changes.

## Layout
- Sheet: 1000 × 720 (`WideFormSizing`); iOS fits it inside the window. Fill `--sheetBackground` (#0E1621).
- Sidebar, 320 wide, on `GradientBackground` with the world map. It scrolls.
  - Header: "Settings" (`SETTINGS.HEADER.TITLE`), `H4`, leading. Close at the trailing end: SF `xmark` 14 semibold, `--icon-primary`, in a 32 × 32 circle of white 10 % (no token). Padding sides 20, top 24, bottom 12.
  - Premium row: `GradientBorderCard`, width `320 × 0.915` (292.8), height 76, padding sides 16, gap 14. `assets/Logos/Premium.png` 48 × 48, title `Subtitle1` ("Get Premium Now", or "Premium User" for premium users). Bottom gap 12.
  - Section card: `GradientBorderCard`, width 292.8, rows with a `RowSeparator` between them.
  - Restore: "Restore purchases" (`SETTINGS.RESTORE_BUTTON`), `Body1`, `--text-secondary`, height 52, bottom padding 20.
- Divider: 1 wide, white 9 % (`--columnDivider`).
- Detail: the rest of the width, padding leading 24. Layout width `min(560, max(width − 321, 320))` (560 in the 1000 sheet). No back or close button on its first page (`hidesPageExit`).

## Sidebar row
Height 60, padding sides 14, gap 14.
- Icon: the asset at 22 × 22 in its own colours, in a 38 × 38 rounded square (radius 10, continuous) of white 8 % (no token).
- Title: `Body1`.
- Trailing: SF `chevron.right` 13 semibold, `--text-secondary`, for rows with a pane. SF `arrow.up.forward` 13 medium, `--text-secondary`, for rows that act at once.
- Selected: fill `--background-tertiary` at 16 % (lightGreen), radius 14 continuous, inset 6 from each side.

| Row | Key | Icon | Pane |
|---|---|---|---|
| Rate us | `SETTINGS.LINKS.RATE` | `Icons/Heart.svg` | none: opens the App Store review prompt |
| FAQ | `SETTINGS.LINKS.FAQ` | `Icons/Faq.svg` | FAQScreen, then a DocumentScreen (back shown) |
| Support | `SETTINGS.LINKS.SUPPORT` | `Icons/Support.svg` | ReportScreen at width 540 |
| Privacy Policy | `SETTINGS.LINKS.PRIVACY` | `Icons/Privacy-Policy.svg` | DocumentScreen `privacy` |
| Terms of Use | `SETTINGS.LINKS.TERMS` | `Icons/Terms.svg` | DocumentScreen `terms` |
| Protocols | `SETTINGS.LINKS.PROTOCOL` | `Icons/Protocol.svg` | Protocols screen (see ProtocolRow). **The default pane.** |

## iPad type
Type scales ×1.3: `H4` 44.2 / 48.6, `Subtitle1` 22.1 / 24.8, `Body1` 19.5 / 27.3. Sizes, paddings and icons do not scale.

## States
- Default: Protocols selected.
- A row with a pane: selected highlight, the pane shows on the right.
- Rate us: acts; no selection change.
- Premium row and Restore: open the paywall / restore purchases.

## Right-to-left
The sidebar moves to the right and the divider with it. Titles are right-aligned. `chevron.right` mirrors (`flipsForRightToLeftLayoutDirection(true)`). `arrow.up.forward` mirrors as an SF "forward" symbol (the iPad Settings screenshot in Arabic shows it pointing up-left). The close button is at the top-left. The detail padding (leading 24) is on the right side of the pane.
- In Arabic the premium title "احصل على المميز الآن" wraps to two lines in the 76-high row (there is about 199 for the text at 22.1). The row height is fixed, so check on a device that nothing is cut off.

## Notes
- Vertical positions: the preview draws the sheet at 1000 × 720 with no window around it. On an 834 pt iPad in portrait the system fits the sheet to the window; see Settings on the iPad page of the screen canvas.
- The preview shows FAQ selected so the pane can reuse the FAQ list. The default pane, Protocols, is in the ProtocolRow preview.
- SF Symbols are not in the repo; the preview draws simple stand-ins. The bar over the pane is a stand-in (see LargeTitleBar).
