# ServerItem

A server / location row in the iPhone server list (and the iPad server column when it uses `ServerListScreen`). It includes three small parts from the same file: `PremiumMark`, `ServerSignal` and `RadioButton`.

Source: `UI/ServerListScreen.swift`.

## Anatomy (at layout width `lw`; values at lw 390)
- Row height `lw × 0.86 / 5.32` (63.0). Side padding `lw × 0.07` (27.3). The whole row is the tap target.
- Leading: flag 35 × 35 (`assets/Flags/<CODE>.svg`, `EARTH` when the code has no flag), gap 20, name `Body1`, one line.
- At least 20 pt of space.
- Trailing, gap 20: [PremiumMark] · ServerSignal · RadioButton. Both gaps become 12 when the PremiumMark shows.

### PremiumMark
"PREMIUM" (`SERVER_LIST.PREMIUM_MARK`, Arabic "مميز") in `Caption`, colour `--bgGraphit`, padding 2 / 6, capsule fill `--gradient-radialOrange`. Shows on a premium server when the user is not premium.

### ServerSignal
Four bars, `size = row height × 0.4` (25.2) square, bottom-aligned. Bar width `size × 0.1667`, gap half of that, radius 2, heights `size ×` 0.1667, 0.375, 0.5833, 0.7917. Filled bars: 4 on a premium server, 2 on a free one. Fill colour `--background-tertiary` (lightGreen); `--text-error` (lightRed) on the Auto server. Empty bars use `--gradient-border`.

### RadioButton
Diameter `row height × 0.4667` (29.4). Green on a free server, orange on a premium one. See the RadioButton card.

## Props
`server` (name, flag code, isPremium, isAuto), `isSelected`, `showsPremiumMark`, `onTap`.

## States
- Selected: the radio fills.
- Not selected.
- Premium server, free user: tap opens the premium offer (ServerNeedsPremiumBanner / paywall), not a server change.
- Tapping the selected row does nothing.

## Right-to-left
The row mirrors: flag and name on the right; mark, signal and radio on the left. The signal bars mirror with the row, so the tallest bar is on the left (the iPhone server-list screenshots in Arabic show this). Long Arabic names ("المملكة المتحدة", "الولايات المتحدة") must fit on one line.
