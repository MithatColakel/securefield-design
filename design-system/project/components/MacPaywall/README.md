# MacPaywall

The Mac paywall: a one-column sheet in the main window. Our own SwiftUI screen (AdaptyUI Flow does not run on macOS). Products, prices and trial terms come from the same Adapty placement as on the iPhone; every price is the store's own string. App Review 3.1.2 needs: price, period, trial terms, auto-renew text, Restore, Terms and Privacy.

Source: `native/MacApp/MacPaywall.swift`. Shown by `MacRootView` as the `.paywall` sheet.

## Layout
Sheet 480 × 640. `ScrollView` (indicators hidden), `VStack` spacing 16, 24 side padding, 16 bottom.
- Background: `LinearGradient([#0F3A4D, graphite, black], .top → .bottom)` = `--gradient-macPaywall` (`--paywallTop`, `--bgGraphit`, `--bgBlack`).
- Close: `xmark.circle.fill` 22, steel (`--auroMetalGray`), padding 14, top trailing. Esc closes.
1. `App-Logo.png` height 34, 28 top padding.
2. Title: remote title, or `paywall.title`, in `headline` (NAMU-1850 22), centred.
3. Features (`VStack` 10, leading): symbol 14 semibold `--lightGreen` in a 26 circle of lightGreen 14 %, then `body`. Remote features use `checkmark`; the fallback list uses `bolt.fill`, `globe`, `shield.lefthalf.filled`, `wand.and.stars`.
4. `paywall.mac` in `body`, `--lightGray`, centred.
5. Plans (state `loaded`):
   - Plan card: padding 16, `RoundedRectangle(16, .continuous)`. Selected: fill lightYellow 8 %, 2 pt `--lightYellow` border. Other: `--surface`, 1 pt `--hairline`.
   - Radio 20: 2 pt ring `--lightYellow` (selected) / steel; selected disc `--lightYellow` inset 4.
   - Name in `subtitle` (NAMU 17) + Badge "Best offer" on the yearly plan. With a trial: trial line `bodyBold` `--lightGreen`, then "Then … / year" `caption` `--lightGray`. Without: price `body` `--lightGray`.
   - Per-month price, trailing, `caption` `--lightGray`.
   - Buy button: PremiumButtonStyle, height 52 ("Start … free trial" or "Subscribe"); a small spinner while busy; Return buys.
6. Message after a purchase or restore: `caption`, `--lightYellow`, centred.
7. Links (`HStack` 18): Restore, Terms of Use, Privacy Policy; `caption`, `--lightGreen`.
8. Fine print: `caption`, `--mediumGray`, centred.

## States
- `loaded` (above). The first plan is selected by default.
- `idle` / `loading`: system spinner (40 vertical padding), "Loading plans…" `body` `--lightGray`.
- `failed`: message `body` `--lightGray`, "Try again" OutlineButtonStyle.

## Fit
With plans loaded, the content is taller than 640: the fine print is below the fold, and the user scrolls to it. The preview clips at 640 to show this. The render uses fallback fonts; check the fold on a Mac screenshot.

## Right-to-left
The column mirrors: close button top-left, features and plan cards right-to-left. Prices keep the store's own string.

## Stand-ins and samples
Prices ($39.99 / year, $3.33 / month, $9.99 / month) and the trial length (3 days) are samples. SF Symbols and the spinner are stand-ins. The two-column `PaywallView` in `native/Design/FlowViews.swift` is not used on `main@00e1b7b`.
