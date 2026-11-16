# RadialGradientButton

The primary call to action on iPhone and iPad: a NAMU-1850 label on a radial green fill. It is the "Continue", "Accept and continue", "Send" and "Get Premium" button.

Source: `UI/RadialGradientButton.swift`, `UI/SVGRadialGradient.swift`, `UI/PressableButtonStyle.swift`.

## Anatomy
- Fill: `--gradient-controlGreen` (green) or `--gradient-controlNeutral` (neutral). Exact CSS of `SVGRadialGradient.control`.
- Border: 1px `--border-primary` (white) at 10 %, inside.
- Label: NAMU-1850, 17 (default `fontSize`), `--text-primary`, one line, centred. The app nudges the label to centre the cap height (`capCentringOffset`); the preview does not.

## Sizes (at layout width `lw`)
| Size | Width | Height | Radius |
|---|---|---|---|
| `large` (default) | lw × 0.83 (max 460 on iPad) | width / 4.64 | 24 (`--radius-button`) |
| `small` | lw × 0.277 | width / 1.763 | 20 (`--radius-buttonSmall`) |
| `fill(height, cornerRadius)` | container | given | given (Report "No problem to report": 56 / 18, font 15) |

At lw 390: large 323.7 × 69.8; small 108.0 × 61.3.

## States
- Default.
- Pressed: scale 0.97, opacity 0.85 (`--opacity-pressed`), spring 0.25 / 0.7.
- Disabled: opacity 0.45 (`--opacity-disabled`); for example "Send" before a rating is chosen, or while a purchase loads.

## Use
- One per screen, at the bottom: onboarding, paywall (Continue), privacy consent, premium pop-up, advertisement (Get Premium), update required, rating sheet (Send), report ("No problem to report", `fill`).
- `neutral` and `small` exist in the code but no screen on `main` uses them.

## Right-to-left
The label is centred; nothing mirrors. Arabic labels use the system Arabic font (NAMU-1850 has no Arabic glyphs).

## Contrast
White text on the light end of the green fill is low contrast. See the README contrast table.
