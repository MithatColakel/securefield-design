# MacButtons

The Mac button styles: Primary, Premium, Outline, and the menu bar panel's Connect button.

Source: `native/Design/Brand.swift` (`PrimaryButtonStyle`, `PremiumButtonStyle`, `OutlineButtonStyle`), `native/MacApp/MacPanel.swift` (`ConnectStyle`, private).

## Styles
| Style | Height | Fill | Text | Pressed | Disabled | Where |
|---|---|---|---|---|---|---|
| `PrimaryButtonStyle` | `minHeight` 48 (44 on Report Send) | Capsule, `LinearGradient([lightBlue, green], .leading → .trailing)` = `--gradient-macPrimary` | `bodyBold`, white | opacity 0.85 (`--opacity-pressed`), scale 0.98, ease-out 0.12 s | opacity 0.4 (`--opacity-disabledMac`) | Main window Connect (max width 280), Welcome and Permission (max 320), Report Send |
| `PremiumButtonStyle` | 48, paywall uses 52 | Capsule, `LinearGradient([lightYellow, darkYellow], .top → .bottom)` = `--gradient-premium` | `bodyBold`, `--onPremium` #1B1305 | 0.85, scale 0.98 | none in code (the system dims a disabled button) | Paywall buy button |
| `OutlineButtonStyle` | 44 | Capsule `--surface` (white 6 %), pressed `--surfaceHigh` (white 10 %); 1.5 pt `--hairline` border | `bodyBold`, white | fill change only | none in code | Report Cancel, paywall Try again |
| `ConnectStyle` (panel) | 48 | off: `--gradient-macPrimary`; on (connected or busy): white 10 % + 1.5 pt `--hairline` | `bodyBold`, white | opacity 0.85, no scale | — | Menu bar panel Connect / Disconnect |

All buttons fill the width they get (`maxWidth: .infinity`).

`IconButtonStyle` (40 × 40 circle, `--surface`, symbol 17 semibold lightGray) is in `native/Design/SearchField.swift`, but no view on `main@00e1b7b` uses it. It has no preview.

## Right-to-left
`.leading → .trailing` mirrors: in Arabic the primary gradient starts green-side on the left. The preview shows this (confirmed on the Mac Report screenshots).

## Notes
- Text on these fills: contrast is checked in the README brand book (Contrast). White on the light end of the primary gradient is one of the pairs to measure.
- The type renders with Red Hat Display from `fonts/`. Arabic uses the system Arabic font.
