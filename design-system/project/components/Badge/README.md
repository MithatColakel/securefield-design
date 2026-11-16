# Badge

A small capsule label on the Mac: "Best offer" on the yearly plan, "Recommended" on the Smart protocol.

Source: `native/Design/Brand.swift` (`Badge`), `native/Design/FlowViews.swift` (`LocalBadge`, the same with a string key).

## Anatomy
- Text: `caption` (Red Hat Display 12) in bold weight.
- Padding: 8 horizontal, 3 vertical. Shape: capsule.
- Fill: `LinearGradient(gradient, .top → .bottom)`.

## Variants
| Variant | Fill | Text | Where |
|---|---|---|---|
| default | `--gradient-premium` (lightYellow → darkYellow) | `--onPremium` #1B1305 | Paywall plan card, yearly plan (`paywall.badge.best`) |
| green | `[lightGreen, darkGreen]` top → bottom (`Brand.greenGradient`; the `--gradient-green` token is the 135° iPhone version of the same colours) | white | Settings, Protocols: Smart (`protocol.recommended`) |

## Right-to-left
The badge follows its row. The text and gradient do not mirror.

## Contrast
White 12 bold on lightGreen (#35DF91) is measured in the README brand book (Contrast).
