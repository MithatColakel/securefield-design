# WideServerList

The iPad server column. It shows on the left of the main screen when the window is 700 pt wide or more (`WideLayout.twoColumnMinWidth`). It stays on screen next to the connect screen. It contains `WideServerRow`. The iPhone list (`ServerItem`) is not changed by it.

Source: `UI/WideServerList.swift`, column width from `UI/WideLayout.swift` (`listWidth = min(max(window × 0.36, 300), 400)`).

## Anatomy
- Background: `GradientBackground`.
- Title "Server location" (`SERVER_LIST.HEADER.TITLE`), `H4`, leading. Padding 20 horizontal, 28 top, 12 bottom.
- Search field: height 44, padding 12 horizontal, radius 12 (`--radius-field`), fill `--fieldFill` (white 8 %). Magnifier icon and placeholder "Search locations" (`IPAD.SERVERS.SEARCH`) in `--text-tertiary`. Input text: system font 17, `--text-primary`. A clear button (`xmark.circle.fill`, `--text-tertiary`) shows when the field has text. Outer padding 16 horizontal, 8 bottom.
- List: cards with 18 between them; padding 16 horizontal, 8 top, bottom safe inset + 24.
  1. The Auto row, in its own card, with no header.
  2. "FREE" (`IPAD.SERVERS.FREE`, uppercased) header, `Body2` in `--text-tertiary`.
  3. "PREMIUM" (`IPAD.SERVERS.PREMIUM`, uppercased) header, `Body2` in `--text-quaternary`, after the 16 × 16 `assets/Logos/Premium.png` crown, gap 6.
  - Header padding 8 horizontal; header-to-card gap 8.
  - Each group is a `GradientBorderCard`; rows are split by `RowSeparator`.
- No match: "No location found" (`IPAD.SERVERS.NO_RESULTS`), `Body1` in `--text-tertiary`, centred, 40 from the top.

## WideServerRow
- Height 56, padding 14 horizontal, items gap 14. The whole row is the tap target.
- Flag 32 × 32 (`assets/Flags/<CODE>.svg`, `EARTH` when there is no flag). Name `Body1`, one line. At least 8 of space.
- Locked (premium server, free user): `lock.fill` symbol, system 13 semibold, `--text-quaternary`.
- `ServerSignal` at size 20: 4 bars on a premium server, 2 on a free one; `--background-tertiary`, `--text-error` on the Auto server.
- Selected: `checkmark.circle.fill`, system 20, `--background-tertiary`, and a row fill of `--background-tertiary` at 16 %, radius 14 (`--radius-rowHighlight`), inset 6 on each side.

## Type size on iPad
`Theme.typography` runs 1.3× on a tablet (`DeviceClass.scaleFont`, rounded to 0.1). In this column `H4` is 44.2 / 48.6 and `Body1` / `Body2` are 19.5 / 27.3. The preview sets these sizes. The search field (system 17) and the symbols do not scale.

## States
- Row: default, selected, locked, locked + selected cannot happen (a locked tap opens the paywall).
- Tap on a locked row: opens the premium offer; the selection does not change. Tap on the selected row: nothing.
- Search: empty, with text (clear button), no results.

## Right-to-left
The column mirrors: title, search icon and flags on the right; signal and check on the left. The signal bars mirror with the row (the iPad main screenshot in Arabic shows this). Arabic: "موقع الخادم", "البحث عن موقع", "مجاني", "بريميوم", "لا يوجد موقع". Uppercasing has no effect on Arabic.

## Preview notes
- Column width 400 px (the cap; a 1180 pt landscape window gives 424.8 → 400).
- `magnifyingglass`, `xmark.circle.fill`, `lock.fill` and `checkmark.circle.fill` are SF Symbols. They are not in the repository. The preview draws simple stand-ins; they are not assets.
- The runner has no SF Pro, so the search field text uses a fallback font.
