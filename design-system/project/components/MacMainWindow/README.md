# MacMainWindow

The Mac main window: a locations sidebar and a detail pane with the connection. Report, Help and Settings are toolbar buttons.

Source: `native/MacApp/MacMainWindow.swift`. Root and sheets: `native/MacApp/MacRootView.swift`. Scene: `Window("Securefield", id: "main")`, default size 920 × 620, `.contentMinSize` (`SecureFieldMacApp.swift:43`).

## Size
Min 820 × 560, ideal 920 × 620. Two fixed columns: sidebar 320, a divider (overlaid `--hairline`), detail fills the rest. No collapse button.

## Sidebar
- Black 25 % over the window background (see MacServerList for the stand-in).
- `App-Logo.png` height 22; padding 16 sides, 12 top.
- SearchField, padding 12.
- Location list (MacServerList) with full names (two lines at most). A locked location opens the paywall.

## Detail (`VStack` spacing 24, padding 24, centred)
1. Spacer.
2. ConnectOrb, size 190. A click toggles.
3. `VStack` 6: StatusLabel; when connected or busy, `FlagView` 18 + location name (`body`, `--lightGray`), spacing 8.
4. Timer: system monospaced 30 semibold. Connected: `HH:MM:SS` in white. Otherwise `––:––:––` in steel (`--auroMetalGray`). Forced left-to-right.
5. Primary button (MacButtons, PrimaryButtonStyle), max width 280: "Connect", or "Disconnect" while connected or busy; disabled while disconnecting. Cmd+Return.
6. Error line after a failed connect: `caption`, `--lightRed`, centred.
7. Spacer.
8. Only without premium: the premium card. `crown.fill` `--lightYellow`; "Get Premium Now" `bodyBold` `--lightYellow`; "Premium is needed to connect." `caption` `--lightGray` (spacing 2); spacer; `chevron.forward` caption `--mediumGray`. Padding 12, max width 420, radius 12, lightYellow 10 % fill, 50 % border. Opens the paywall.
- Background: `[graphite, black]` `.topLeading → .bottomTrailing` (BrandBackground without the map).

## Toolbar (`.primaryAction`)
`exclamationmark.circle` (Report), `questionmark.circle` (FAQ), `gearshape` (Settings window). Each has a tooltip and an accessibility label. macOS draws the title bar and the buttons; the preview draws a simple stand-in.

## Flow and sheets (MacRootView)
- First launch: Welcome → Permission → main; a refused permission shows the denied state. These pages are 480 × 640 on BrandBackground with the map (see MacFirstLaunch).
- Sheets over the window: paywall (MacPaywall), report (MacReportView), FAQ / Privacy / Terms (MacDocumentSheet).
- When the store says "not premium", the window shows the paywall (the Mac app is premium only).

## Right-to-left
The columns swap: the sidebar is on the right. The orb and timer stay left-to-right. Whether macOS also mirrors the title bar (traffic lights, toolbar side) is drawn by the system: the preview keeps the stand-in title bar left-to-right. The Mac screenshots in Arabic show that macOS does not mirror the title bar: the traffic lights stay at the left and the toolbar at the right. The chevron in the premium card has the same double-flip question as in MacPanel.

## In the code, not on any screen on `main@00e1b7b`
These views exist in `native/Design/` but no screen uses them. They get no preview:
- `PaywallView` (two-column paywall, `FlowViews.swift`): the window uses `MacPaywall`.
- `ConnectPanel`, `ConnectPanelCompact`, `ConnectTiles`, `InfoTile` (`ConnectViews.swift`, `SearchField.swift`).
- `IconButtonStyle` (`SearchField.swift`), `ShortcutsList` (`SettingsViews.swift`).
- `MacTestView` ("Connection Test" window) is DEBUG only.

## Stand-ins and samples
SF Symbols are simple stand-ins. Location list, timer and selection are samples. Vertical positions are checked against the Mac screenshots (see the Mac page of the screen canvas).
