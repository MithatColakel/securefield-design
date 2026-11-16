# GradientBackground

The ground of every SecureField screen on iPhone and iPad: a diagonal gradient from `bgGraphit` to `bgBlack`, optionally with the world map on top in `overlay` blend mode.

Source: `UI/GradientBackground.swift`.

## Use
- Put it behind every full screen. Content sizes itself; the background never changes the layout size.
- `gradientOnly` (default): settings, server list, protocols, report, documents.
- `withBackgroundImage`: the main (Connect) screen and the paywall. The map is `assets/Images/World-Map.png`, `object-fit: cover`, `mix-blend-mode: overlay`.
- The gradient is `--gradient-background` (top-leading to bottom-trailing, 135deg). A screen can pass other colours; the code only passes the default.

## Do / don't
- Do use `overlay` blend for the map. Plain opacity makes the screen flat and grey.
- Don't put the map in front of content or let it take taps.
- The Mac app uses its own `BrandBackground` (see that card).

## States
None. It is static.

## Right-to-left
The whole UI follows the locale, so `startPoint: .topLeading` becomes top-right in Arabic. The Arabic preview runs the diagonal from top-right to bottom-left (225deg). The map image does not mirror.
