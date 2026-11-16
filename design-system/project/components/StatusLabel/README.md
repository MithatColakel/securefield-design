# StatusLabel

The Mac connection status text under the Connect orb.

Source: `native/Design/ConnectViews.swift` (`StatusLabel`).

## Anatomy
- `VStack` spacing 6, centred.
- Status in `title` (NAMU-1850 28): `status.connected` in `--lightGreen`; `status.connecting`, `status.disconnecting`, `status.disconnected` in white.
- Only when disconnected: the hint in `body`, `--lightGray`: `hint.click` ("Click to connect") on the Mac.
- Changes animate (ease-in-out 0.2 s).

## Where
Main window detail column, under the orb. In the window, when connected or busy, a row with `FlagView` 18 and the location name (`body`, `--lightGray`, spacing 8) follows under it (see MacMainWindow).

The menu bar panel does not use StatusLabel: it shows a dot and the status in `caption` (see MacPanel).

## Fonts
NAMU-1850 is `fonts/NAMU-1850.ttf`.
