# SplashScreen

The launch screen on iPhone and iPad: the animated Securefield logo and a progress bar while the app starts.

Source: `UI/SplashScreen.swift`. Assets: `assets/Logos/Splash.png` (image `Splash`), `assets/Lotties/Logo.json`.

## Layout (screen `w` × `h`, full screen, ignores the safe area)
- Ground: `--gradient-background`, then `Splash.png` scaled to fill, clipped.
- Logo: Lottie `Logo` (1246 × 600, 24 fps, 54 frames), frame `w × 0.75` by `h × 0.5`, centre at `(w / 2, h / 2 − h × 0.07)`. Plays once and holds the last frame.
- Progress bar: width `w × 0.5`, height 6, capsule, centre at `(w / 2, h × 0.75)`.
  - Track: `#3F4751` literal in code (same value as `--darkGray`).
  - Fill: `#34DC8F` literal (`--splashFill`). Not `lightGreen` (#35DF91).

## States
- Bar fades in (0.3 s ease-in), then creeps to 40 % over 4 s (ease-out).
- Real progress moves it forward (0.8 s ease-in-out).
- At 100 %: holds 0.3 s, then the whole screen fades out (0.5 s).

## Right-to-left
No text. The bar fills from the leading edge (ZStack `.leading`), so in Arabic it fills from the right (normal SwiftUI mirroring, **to confirm** on a device). The third preview screen shows the Arabic fill from the right (40 %).

## Notes
- Vertical positions: this component preview (390 × 844) uses top inset 0. On the device the content starts below the system top inset, and the bottom comes from the window's safe area. The screen cards in the Screens group show this (47 pt top inset on a 390 × 844 iPhone, or the system sheet edge) and are checked against screenshots where one exists.
- The preview needs network access (pinned `lottie-web@5.12.2` from jsDelivr) and HTTP, not `file://`.
