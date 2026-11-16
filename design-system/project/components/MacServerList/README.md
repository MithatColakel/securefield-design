# MacServerList

The Mac location list: one `ServerRow` per location, used in the main window sidebar and in the menu bar panel's picker. Includes `FlagView` and `SignalBars`.

Source: `native/Design/ConnectViews.swift` (`ServerRow`, `ServerListView`), `native/Design/Brand.swift` (`FlagView`, `SignalBars`).

## ServerRow (left to right)
1. `FlagView` 30: the flag file (`assets/Flags/<code>.svg`), `scaledToFill`, clipped to a circle, 1 pt ring white 25 % (`--highlight`).
2. Name: `bodyBold`, white. One line (panel picker) or two lines at most (`fullName`, main window). Under the Auto row (`EARTH`): "Fastest" in `caption`, `--lightGreen`. Spacing 2.
3. Spacer, at least 4.
4. Premium rows only: SF Symbol 12 pt, `--lightYellow`: `lock.fill` when the user has no premium, `crown.fill` when they have it.
5. `SignalBars`: 3 bars, 4 wide, 6 / 10 / 14 high, gap 2, radius 1.5; lit bars `--lightGreen`, others white 20 %. 1 to 3 lit (`signal`). Hidden from accessibility.
6. Radio 18 × 18: 2 pt ring, `--lightGreen` when selected, else `--auroMetalGray` (`Brand.steel` #6D767D); selected adds a `--lightGreen` disc inset 4.
- Row: `HStack` spacing 12, 6 vertical padding.

## ServerListView
- `LazyVStack` spacing 2; 8 side padding, 16 bottom. Scroll indicators hidden.
- Each row: 12 side padding; selected row on `RoundedRectangle(10, .continuous)` white 8 % (`--fieldFill`).
- A locked row asks for the paywall; other rows select.
- Empty search: "No location found" in `body`, `--mediumGray`, padding 16.
- The live list is the backend's list in the backend's order, with no headers. Only the stand-in list of the design screenshots shows "Quick Access" and "All locations" headers (`caption`, `--mediumGray`, padding 12 / 12 top / 4 bottom). The preview shows them only as a note.

## Where
- Main window sidebar, 320 wide, `fullNames: true`.
- Menu bar panel picker, 300 high, clipped to radius 12.

## Right-to-left
The row mirrors: the flag is on the right, the radio on the left. The bars keep their order (shortest first in reading direction) under normal SwiftUI mirroring; the Mac screenshots in Arabic confirm the mirrored row.

## Stand-ins and samples
`lock.fill` and `crown.fill` are SF Symbols, not in the repo: simple stand-ins. The locations and signal levels are samples (`DesignLocation.all`).

## Background
In the main window the sidebar is black 25 % over the system window background, which the code does not set. The Mac screenshots show #161616 there; the main-window screen card uses this measured value.
