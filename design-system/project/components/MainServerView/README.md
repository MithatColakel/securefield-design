# MainServerView

The panel at the bottom of the iPhone main screen. It shows the selected server and opens the server list.

Source: `UI/MainScreen.swift` (`MainServerView`).

## Anatomy
- Surface: GradientBorderCard, radius 28, `topCornersOnly`. Height `layoutWidth / 3.15` (123.8 at lw 390), including 12 pt top padding and the device bottom inset.
- Grabber: 60 × 4, radius 3, `--background-indicator` (darkCharcoal), shadow `--shadow-grabber`. 20 pt above the row.
- Row: 28 pt side padding. Row width = layoutWidth − 56.
  - 80 %: flag 35 × 35 (`assets/Flags/<CODE>.svg`, EARTH when missing), 20 pt gap, server name `Body1`, one line, tail truncation.
  - 20 %: "Change" (`MAIN.SERVER_VIEW.BUTTON`) in `Body2` (lightGreen), centred.

## Props
`server` (name, flag code), `onSelect`.

## States
One state. Tap "Change" to open the server list. On iPad (two columns) the server list is a column instead, and this panel is not shown.

## Right-to-left
The flag and name are on the right, "Change" on the left. Long Arabic names ("المملكة المتحدة") must fit; they truncate at the tail.

## Notes
- **Vertical positions to confirm.** The preview uses bottom inset 0, so the panel is drawn without the device bottom inset. The height is checked against device screenshots.
