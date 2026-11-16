# PremiumPopUp

The shorter premium offer. It opens from a premium server row (with `ServerNeedsPremiumBanner`) and from other premium prompts (without it). Includes `ServerNeedsPremiumBanner` and `PremiumFeatureItem`.

Source: `UI/PremiumPopUpScreen.swift`.

## Layout (screen width `W`, top area = height above the bottom stack)
- Background: `GradientBackground` (gradient only, no map).
- Upper band: `top area × 0.68` (0.58 on a tablet), content centred vertically. Column, gap 20 (8 with a server banner):
  - `RestoreCloseHeader` with "Restore" (`PREMIUM_POP_UP.RESTORE_BUTTON`), then `assets/Logos/Premium.png`, square: `W × 0.448`; `W × 0.2` with a server banner; `W × 0.28` on a tablet.
  - Column, gap 32 (16 with a banner): [ServerNeedsPremiumBanner], title "Experience Premium Service" (`PREMIUM_POP_UP.TITLE`) in `H6`, `--text-primary`, centred; then the three PremiumFeatureItems, gap 8, leading-aligned.
- Cards: the rest of the top area, `PremiumCard` × products spread evenly (as on PremiumScreen).
- Bottom stack: as PremiumScreen. Button "Continue" (`PREMIUM_POP_UP.BUTTON`), or "Try again"; `LegalFooter`.
- `LoadingOverlay` while loading or busy.

## ServerNeedsPremiumBanner
- "{{server}} needs Premium." (`PREMIUM_POP_UP.SERVER_TITLE`) in `Body2`, `--text-primary`, centred; then gap 4, "Subscribe to connect to this server." (`SERVER_SUBTITLE`) in `Caption`, `--text-tertiary`, centred.
- Padding 16 / 8. Full width minus 24 on each side. Fill `--background-secondary`, radius 12, 1 pt border `--border-secondary` (lightYellow).

## PremiumFeatureItem
- Row, gap 8: icon 24 × 24 (`Speed`, `World`, `Protection`), text in `Body1`, `--text-quaternary` (lightYellow), then `assets/Icons/Done.svg` 20 × 20.
- Texts: "Ultra-fast connection", "Worldwide locations", "Unlimited protection" (`PREMIUM_POP_UP.DESC_1…3`).

## States
Without server, with server banner; loading / loaded / error as PremiumScreen.

## Right-to-left
Header mirrors. Feature rows: icon on the right, the Done tick after the text (on the left). Arabic: "تجربة الخدمة المميزة", "{{server}} يتطلب اشتراك Premium.", "اشترك للاتصال بهذا الخادم.".

## Preview notes
390 × 844, bottom inset 34. Sample prices. `H6` is NAMU-1850.

## Notes
- Vertical positions: this component preview (390 × 844) uses top inset 0. On the device the content starts below the system top inset, and the bottom comes from the window's safe area. The screen cards in the Screens group show this (47 pt top inset on a 390 × 844 iPhone, or the system sheet edge) and are checked against screenshots where one exists.
