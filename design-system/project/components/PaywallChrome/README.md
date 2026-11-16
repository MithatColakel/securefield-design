# PaywallChrome

Three small parts used around every paywall and offer screen: `RestoreCloseHeader`, `LegalFooter` and `LoadingOverlay`. The paywall layout itself can be a remote flow; these parts are in the app's code.

Source: `UI/PaywallChrome.swift`.

## RestoreCloseHeader
- Height 44, padding 12 horizontal.
- Leading: Close button 64 × 44, icon `assets/Icons/Close.svg` 24 × 24, tinted `--icon-primary` (template rendering).
- Trailing: text button, `Body1` in `--text-secondary` (lightGreen), height 44, padding 8 horizontal. Default "Restore" (`PREMIUM.RESTORE_BUTTON`); a screen can pass another title.
- Used on: PremiumScreen, PremiumPopUpScreen, the onboarding offer.

## LegalFooter
- Three links in a row: "Privacy Policy" (`LEGAL_LINKS.PRIVACY`), "Terms of Use" (`LEGAL_LINKS.TERMS`), "About Subscription" (`LEGAL_LINKS.ABOUT`).
- Text: Red Hat Display Regular with the `Caption` style, `--text-secondary`, centred. Separator "•" in `--separator-primary`, 5 padding on each side.
- Size steps down until the row fits on one line: 12, 11, 10, 9; then size 10 on up to two lines. On a tablet each size is × 1.3.
- Row height 17 (one line). Each link has a 14 vertical hit padding.
- Tap opens the document in a sheet (`DocumentScreen`).
- Used on: PremiumScreen, PremiumPopUpScreen, AdvertisementScreen, Onboarding.

## LoadingOverlay
- Full screen black at 60 %, over the safe areas. It blocks taps.
- Centre: system large circular spinner, tint `--loadingTint` (#5AAD79), in a 75 × 75 box, radius 15 (`--radius-loadingBox`), fill `--loadingBox` (#3A3F46).
- Fades in over 0.5 s (ease out).
- Used while a purchase, restore, report send or product load runs.

## Right-to-left
The header mirrors: Close on the right, Restore on the left. The Close icon is an X and does not mirror. The footer order reverses. Arabic: "استعادة", "سياسة الخصوصية", "شروط الاستخدام", "حول الاشتراك".

## Preview notes
The spinner is a static stand-in for the system spinner.
