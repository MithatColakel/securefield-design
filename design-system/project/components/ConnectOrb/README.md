# ConnectOrb

The Mac Connect button: a round orb drawn in SwiftUI. The iPhone uses Lottie files; the Mac target does not link Lottie, so it draws its own orb with the same colours and the same order of states.

Source: `native/Design/ConnectViews.swift` (`ConnectOrb`). Size `S` = 190 in the main window (`MacMainWindow.swift:66`); the default 220 is used only by `ConnectPanel`, which is not on any screen on `main@00e1b7b`.

## Anatomy (bottom to top), all in fractions of S
1. Glow: a circle, blue #008FF5 at 22 % (green #1EB972 at 35 % when connected), blur radius S × 0.16. Connected: scales 1 → 1.12 and back, ease-in-out 2.4 s, forever.
2. Ring: `strokeBorder`, width S × 0.04, `LinearGradient(.topLeading → .bottomTrailing)`: `Brand.connectGradient` [darkBlue #0073C5, lightBlue #33A9FE, lightGreen #35DF91, mediumGreen #178F59]; connected: `Brand.greenGradient` [lightGreen, darkGreen #198F57].
3. Inner disc: inset S × 0.06, `RadialGradient` `--orbInner` #1E2C40 → `--orbInnerEdge` #0B121C, centre, end radius S × 0.5.
4. Connecting and disconnecting only: an arc, `trim(0, 0.28)` of the full circle, stroke width S × 0.04, round caps, `connectGradient` leading → trailing; it turns 360° in 1.1 s, linear, forever. A centred stroke on the full frame: half of it lies outside the ring.
5. SF Symbol `power`, S × 0.30, semibold, gradient top → bottom (the ring colours).
- Accessibility label: "Connect" / "Disconnect" (English in code, not localised).

## States
`disconnected` → `connecting` → `connected` → `disconnecting`. A tap toggles.

## Right-to-left
The orb forces left-to-right (`ConnectViews.swift:48`). It does not mirror in Arabic.

## Preview notes
- The preview draws the orb in SVG with the code's numbers. The SwiftUI blur radius and the SVG `stdDeviation` are not the same unit; the glow size is close, not exact.
- `power` is an SF Symbol (not in the repo): a simple stand-in.
- Gradient stops are evenly spaced, as SwiftUI does with a colour list.
