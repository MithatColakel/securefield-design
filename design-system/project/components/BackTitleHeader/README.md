# BackTitleHeader

The title bar of the server list on iPhone: a leading icon button and a centred title. Settings, Protocols, FAQ and the documents use the system bar instead (see LargeTitleBar).

Source: `UI/ServerListScreen.swift` (`BackTitleHeader`).

## Anatomy
- Height `layoutWidth / 8.93` (43.7 at lw 390).
- Leading part: 20 % of layout width, icon 24 × 24, tinted `--icon-primary`, 20 pt leading padding.
- Title: `Subtitle1`, centred, multi-line allowed.
- Trailing part: an empty 20 % box, so the title stays centred.
- On the server list, a 0.5 pt rule in `--serverListRule` (white at 0x17/255) sits under it.

## Props
`title`, `icon` (`icons/Back` or `icons/Down`), `onBack`.

## Use
- `icons/Down` on the server list (it is presented from the bottom). This is its only use in release builds.
- `icons/Back` on the network debug screen (debug builds only).

## Right-to-left
The icon is on the right. `icons/Back` mirrors (`flipsForRightToLeftLayoutDirection`); `icons/Down` does not.
