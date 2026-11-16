# ClientNoticeBand

One line under the main screen header (iPhone and iPad). It shows a notice from the server, or, when there is none, that a newer app version is available. It has an Update button and a close button. It takes its own row, so it never covers the Connect button.

Source: `UI/ClientNoticeBand.swift`; placed in `UI/MainScreen.swift` directly under `MainHeader`.

## Use
- Notice from the server (`board.visibleNotice`): the **prominent** row.
- No notice, newer version (`board.visibleUpdate`): the **quiet** row.
- Neither: nothing. The band takes no space.
- The server sends no text, only a kind and parameters. The app words each kind:
  - `updateRecommended`: `CLIENT_NOTICE.UPDATE_RECOMMENDED`.
  - `protocolRetiring`: `CLIENT_NOTICE.PROTOCOL_RETIRING` "{{protocol}} {{generation}} will be retired on {{date}}." The date is a long date in the app language, read in UTC.
  - `protocolRetired`: `CLIENT_NOTICE.PROTOCOL_RETIRED`.
  - Update available: `CLIENT_NOTICE.UPDATE_AVAILABLE` "Version {{version}} is available."
- Protocol names are the app's names: AmneziaWG shows as "Securefield Shield".

## Anatomy
- Outer: horizontal padding 16, top padding 4.
- Row: gap 10; padding leading 12, trailing 4; vertical 8 (prominent) or 2 (quiet).
- Prominent fill: `--background-secondary` (iceBlue 20 %), corner radius 12 (continuous). Quiet: no fill.
- Text: `Caption`, `--text-primary` (prominent) or `--text-tertiary` (quiet, lightGray), leading-aligned, wraps, takes the free width.
- Update: `ALERTS.UPDATE_ALERT.BUTTON` "Update", `Caption`, `--text-secondary` (lightGreen), padding 5 / 10, capsule stroke 1 `--border-quaternary` (lightGreen).
- Close: SF Symbol `xmark`, 11 pt semibold, `--icon-primary` (lightGray), in a 28 × 28 tap area. Accessibility label `CLIENT_NOTICE.DISMISS` "Dismiss".

## States
- Prominent, quiet, hidden (see Use).
- Update opens the store link. Close dismisses that notice (or that version). The row fades out (`.transition(.opacity)`).

## Right-to-left
The row mirrors: text on the right, then Update, then close on the far left. Arabic: "تحديث", "إغلاق". The Arabic notice strings start with a right-to-left mark (U+200F) so a Latin protocol name at the start does not flip the line. Long Arabic text wraps to two lines; nothing is cut.

## Notes
- `xmark` is an SF Symbol, not in the repo. The preview draws a simple stand-in cross.
- Version numbers, generation and date in the preview are samples. The date comes from `Date.FormatStyle(date: .long)` with locale `ar`, which uses Arabic-Indic digits ("١ مارس ٢٠٢٧"); version numbers come from the server as written.
