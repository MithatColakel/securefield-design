# MacPanel

The Mac menu bar panel: the whole day-to-day app. One click connects or disconnects, the location is chosen inline, and Settings, Help, Report and Quit are in the footer. The same view shows in the small window when the user clicks the Dock icon.

Source: `native/MacApp/MacPanel.swift` (`MacPanel`, `ConnectStyle`, `MacMenuLabel`). Scene: `MenuBarExtra` with `.menuBarExtraStyle(.window)` (`SecureFieldMacApp.swift:34`).

## Layout
`VStack` spacing 14, padding 16, width 340. Background: `[graphite, black]` `.topLeading → .bottomTrailing` (see BrandBackground; no map).

1. **Header** (`HStack` 10): `App-Logo.png` height 22; "Securefield" in `subtitle` (NAMU-1850 17; the literal is not localised); spacer; status dot 8 × 8 + status in `caption`.
   - Dot: `--lightGreen` connected, `--lightYellow` connecting / disconnecting, `--auroMetalGray` (steel) not connected.
   - Status text: `--lightGreen` when connected, else `--lightGray`.
2. **Connect block** (`VStack` 10): timer `HH:MM:SS`, system monospaced 34 semibold, 6 top padding, white when connected else steel; it shows `00:00:00` when not connected. Then the Connect button (`ConnectStyle`, see MacButtons): gradient "Connect"; white 10 % + hairline "Disconnect" while connected or busy. An error line (`caption`, `--lightRed`) shows under it after a failed connect.
3. **Location row**: `FlagView` 24, name `bodyBold` (one line), spacer, `chevron.forward` (caption size, `--mediumGray`). Padding 12, `RoundedRectangle(12)` `--surface` + `--hairline`. Opens the picker.
4. **Premium strip** (only when the store says "not premium"): `crown.fill` `--lightYellow`; "Get Premium Now" `bodyBold` `--lightYellow`; "Premium is needed to connect." `caption` `--lightGray`; spacing 1. Padding 12, radius 12, fill lightYellow 10 %, 1 pt border lightYellow 50 %. Opens the paywall in the main window.
5. **Divider**, overlaid with `--hairline`.
6. **Footer** (`HStack` 4): `gearshape` (Settings window), `questionmark.circle` (FAQ), `exclamationmark.circle` (Report), spacer, `power` (Quit). Each 15 pt `--lightGray` in a 32 × 28 hit area, with a tooltip and accessibility label.

## Picker state
Replaces items 2–4: a header (`chevron.backward` `--lightGray` in 28 × 28, "All locations…" in `subtitle`), SearchField, then the location list (MacServerList) 300 high, clipped to radius 12. Picking a location closes the picker and clears the search.

## Menu bar item (`MacMenuLabel`)
SF Symbol 15 pt semibold: `shield` as a template image when idle (the system tints it); `checkmark.shield.fill` in `--lightGreen` when connected, in `--lightYellow` while connecting. Not shown in the preview.

## States in the preview
Not connected, connecting, connected, not premium (strip), picker open; Arabic: connected, not premium, picker.

## Right-to-left
The panel mirrors (header, rows, footer order). The timer forces left-to-right. Chevrons: one `chevron.forward` / `chevron.backward`, mirrored in Arabic (no double turn). Back points right and forward points left in Arabic, as the Mac screenshots show.

## Stand-ins
- SF Symbols (crown, chevrons, gear, question, exclamation, power) are not in the repo: simple stand-ins.
- The panel window frame and corner radius are drawn by macOS; the preview rounds the corners as a stand-in.
- Timer value and location are samples. The timer font is the system monospaced font; the runner has none of Apple's fonts.
- Vertical positions are checked against the Mac screenshots (see the Mac page of the screen canvas).
