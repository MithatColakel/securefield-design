# MainConnectButton

The Connect button in the middle of the iPhone and iPad main screen. Its face is a Lottie animation; a drawn ring shows connecting progress.

Source: `UI/MainConnectButton.swift`, Lotties `Resources/Lotties/Connect/TTC.json` (to connected) and `TTD.json` (to disconnected), copied to `assets/Lotties/`.

## Anatomy
- Size: square, `layoutWidth × 0.53` (206.7 at lw 390).
- Face: Lottie, 450 × 450, 24 fps, 37 frames (TTC). The app shows TTD's last frame when idle and TTC's last frame when connected; between them it plays the animation once.
- Connecting ring: stroke 6 pt, round caps, centre-line diameter `size × 0.89 − 6`, angular gradient `--gradient-connectButton` (darkBlue 16 %, lightBlue 41.3 %, lightGreen 57.5 %, mediumGreen 80.2 %), starting at 12 o'clock and growing clockwise. The preview has square caps (CSS mask), not round.
- The button is always laid out left to right, also in Arabic.

## States (`DisplayStatus`)
| State | Face | Ring |
|---|---|---|
| disconnected | TTD, last frame | hidden |
| connecting | TTD (switches back from TTC if needed) | fades in (0.1 s), grows from 0 to full over 40 s |
| connected | ring completes (0.3 s × the rest), fades out (0.5 s), then TTC plays | hidden |
| disconnecting | ring fades out, then TTD plays | hidden |

If the app opens already connected, it shows TTC's last frame with no animation.

## Interaction
- Pressed: opacity 0.8 (`--opacity-connectPressed`), no scale. A light haptic on tap.
- One tap toggles connect or disconnect. The status text below it (ConnectionStatusText) names the state.

## Do / don't
- Don't redraw the face. Use the Lottie files.
- Don't mirror the button or the ring direction in Arabic.

## Preview
The preview loads the local copy of `lottie-web` 5.12.2 (`vendor/lottie-web-5.12.2/`, MIT licence file beside it) and the two Lottie files by relative path. It needs no network. Over `file://` the browser blocks the Lottie files; open it over HTTP (the design page does). The app itself bundles Lottie.
