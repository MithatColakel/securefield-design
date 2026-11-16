# RadioButton

The round selection mark in server rows and protocol rows on iPhone and iPad.

Source: `UI/ServerListScreen.swift` (`RadioButton`), `UI/SVGRadialGradient.swift` (`.radio`).

## Anatomy (bottom to top)
1. Disc: `--background-secondary` (iceBlue 20 %).
2. Inner highlight: 2 pt white @ 25 % stroke, blur 1, offset (−1, −1), masked to the bottom-trailing half. Not drawn in the preview.
3. Selected fill (opacity 0 → 1): `SVGRadialGradient.radio`, stops 0.22892 / 0.633438, transform translate(10.8889, 5.25) rotate(82.614) scale(28.2343, 33.714) in points. CSS has no equal; the preview uses an SVG `radialGradient` with the same numbers.
4. 1 pt ring: `--border-tertiary` (white) at 10 %.
5. `orange` only: a 1 pt `--border-secondary` (lightYellow) ring, also when off.
6. Tick (`withTick` and selected): `assets/Icons/Tick.svg` at 45 % of the diameter, ink #171D2E (in the file).

## Variants
| Variant | Fill when on | Extra ring | Where |
|---|---|---|---|
| `green` | `--gradient-green` colours | — | free server rows, protocol rows (with tick), ad step indicator |
| `orange` | `--gradient-radialOrange` colours | lightYellow | premium server rows |
| `grayOrange` | `--gradient-radialOrange` colours | — | paywall plan cards (PremiumCard) |

## Props
`isSelected`, `variant`, `diameter` (server rows: row height × 0.4667), `withTick`.

## Right-to-left
No change. The gradient does not mirror.
