# SettingsPremiumCard

The offer card at the top of Settings on iPhone. It opens the premium offer. A premium user sees the same card with the title "Premium User".

Source: `UI/SettingsScreen.swift` (`SettingsPremiumCard`). On iPad (two columns) Settings is `WideSettingsView`, which uses the same card in its sidebar.

## Anatomy (layout width `lw`; values at lw 390)
- A `GradientBorderCard`, width `lw × 0.915` (356.9), height `width / 1.367` (261.1). The whole card is one button.
- Inside the border: its own fill `--gradient-backgroundOpacity` (bgGraphit 20 % → bgBlack 20 %, top-leading → bottom-trailing), over the card's `--background-secondary`.
- Top half (centred, gap 4): `assets/Logos/Premium.png` at `lw × 0.233` square (90.9), then the title in `Subtitle1`, `--text-primary`, centred.
  - Free user: "Get Premium Now" (`SETTINGS.CARD.TITLE`). Premium user: "Premium User" (`SETTINGS.CARD.TITLE_PREMIUM`).
- Bottom half: three feature lines, gap 14, in a column `lw × 0.915 × 0.41` wide (146.3), leading-aligned, centred in the card.
  - Each line: 20 × 20 icon, gap 16, text in `Caption`, `--text-primary`.
  - `assets/Icons/Speed.svg` "Ultra-fast connection" (`SETTINGS.CARD.DESC_1`), `assets/Icons/World.svg` "Worldwide locations" (`DESC_2`), `assets/Icons/Protection.svg` "Unlimited protection" (`DESC_3`).

## States
- Free user, premium user (title only changes).
- Pressed: the system plain-button press.

## Right-to-left
Icons stay on the leading side, so they move to the right. The icons do not mirror. Arabic: "احصل على المميز الآن", "اتصال فائق السرعة", "مواقع عالمية", "حماية غير محدودة". The 146.3 column is narrow: Arabic lines must fit on one line; they do in the preview.

## Preview notes
`Subtitle1` is NAMU-1850 (`fonts/NAMU-1850.ttf`).
