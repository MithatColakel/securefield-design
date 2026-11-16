# PremiumScreen

The app's own paywall on iPhone and iPad. It shows when a remote paywall flow cannot render, and for push offers. It is a sheet. Built from `RestoreCloseHeader`, the premium logo, `PremiumCard` × products, `RadialGradientButton`, `LegalFooter` and `LoadingOverlay`.

Source: `UI/PremiumScreen.swift`; presented from `UI/MainScreen.swift` and `Push/PromotionPresenter.swift`.

## Layout (screen height `H`, width `W`)
- Background: `GradientBackground`, variant `withBackgroundImage`.
- Top area (all height above the bottom stack):
  - Band: `top area × 0.54` (0.44 on a tablet), content centred vertically. Centred column, gap 8: `RestoreCloseHeader` (44), then `assets/Logos/Premium.png`, square, side `min(W × 0.71, band − 52)` (`W × 0.42` on a tablet).
  - Cards: the rest of the top area. Each `PremiumCard` has equal flexible space above and below, so the cards spread evenly. They arrive with a fade and a 20 pt rise, 0.4 s ease-out, 0.15 s apart.
- Bottom stack, gap 20, padding 24 horizontal, bottom `max(safe inset, 16)`:
  - `RadialGradientButton` (large, green): "Continue" (`PREMIUM.BUTTON`). "Try again" (`PREMIUM.RETRY_BUTTON`) when the products failed to load. Disabled (opacity 0.45) while they load.
  - `LegalFooter`.
- `LoadingOverlay` over everything while products load or a purchase / restore runs.

## States
- Loading: no cards, button disabled, overlay on.
- Loaded: cards, first card selected.
- Error: no cards, button "Try again". Pressing Continue with no products shows the alert "Couldn't load subscriptions".
- Purchase / restore running: overlay on.
- Alerts (system): "Purchase restored", "No purchase found", "Restore failed", "Purchase failed", "Purchase pending", "Payment received", "You're premium".
- The screen closes itself when the user becomes premium.

## Right-to-left
Header mirrors (Close right, Restore left). Cards mirror (see PremiumCard). Logo and button are centred.

## Preview notes
390 × 844, bottom inset 34, no top inset. Sample prices. Spinner and alerts not shown.

## Notes
- Vertical positions: this component preview (390 × 844) uses top inset 0. On the device the content starts below the system top inset, and the bottom comes from the window's safe area. The screen cards in the Screens group show this (47 pt top inset on a 390 × 844 iPhone, or the system sheet edge) and are checked against screenshots where one exists.
