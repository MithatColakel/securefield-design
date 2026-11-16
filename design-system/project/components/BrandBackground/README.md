# BrandBackground

The Mac page background: a graphite-to-black diagonal gradient with the world map blended over it.

Source: `native/Design/Brand.swift` (`BrandBackground`, `Brand.backgroundGradient`).

## Anatomy
1. `LinearGradient([graphite, black], .topLeading → .bottomTrailing)`: `--bgGraphit` #172231 → `--bgBlack` #000000. SwiftUI maps the points in unit space, so the CSS equal is `linear-gradient(to bottom right, …)`. The `--gradient-background` token is written as 135deg, which is the same only on a square.
2. `assets/Images/World-Map.png`, `scaledToFill`, blend mode overlay (`showsMap`, default true).
3. Clipped, ignores the safe area, no hit testing.

## Where
- With the map: the first-launch steps in the main window (`MacRootView.centered`: WelcomeView, PermissionView, denied state), window 480 × 640.
- The main window detail column and the menu bar panel draw only the gradient (no map), with the same colours and points (`MacMainWindow.swift:97`, `MacPanel.swift:194`).
- iPhone and iPad use their own `GradientBackground` (see that component).

## Right-to-left
`.topLeading` becomes the top-right corner in a right-to-left layout: the whole UI follows the locale. The Mac screenshots in Arabic show the dark corner at the top left.
