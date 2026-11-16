# ActionsCard

The list of settings links on iPhone: one `GradientBorderCard` with an `ActionRow` per action, split by `RowSeparator`. Below the SettingsPremiumCard and the "Restore purchases" button.

Source: `UI/SettingsScreen.swift` (`SettingsScreen`, `ActionsCard`, `ActionRow`, `SettingsAction`).

## Settings screen order (layout width `lw`)
1. `SettingsPremiumCard`, 16 from the top.
2. "Restore purchases" (`SETTINGS.RESTORE_BUTTON`): a text button, `Body1` in `--text-secondary` (lightGreen), centred, row height `lw × 0.915 / 6.47` (55.2 at lw 390).
3. `ActionsCard`. Column width `lw × 0.915`, centred; 100 bottom padding. Title bar: `LargeTitleBar` "Settings".

## ActionsCard
- Height `lw × 0.915 / 0.765 / 8 × rows` (6 rows: 349.9 at lw 390). Rows share it equally. The 8 is the row count the design was drawn for; the card stays the same height per row with fewer rows.
- Rows in order (`SettingsAction.listed`): Rate us (`icons/Heart`), FAQ (`icons/Faq`), Support (`icons/Support`), Privacy Policy (`icons/Privacy-Policy`), Terms of Use (`icons/Terms`), Protocols (`icons/Protocol`). A debug build adds a seventh row (Network debug, `icons/Speed`); it is not in the shipped app.

## ActionRow
- Padding 16 horizontal. The whole row is the tap target.
- Leading group (padding 4, gap 16): 24 × 24 icon from `assets/Icons/`, title in `Body1`, `--text-primary`.
- Trailing: `assets/Icons/Next.svg`, 24 × 24. It mirrors in right-to-left (`flipsForRightToLeftLayoutDirection`).

## States
Default; pressed (system plain-button press). No selected state.

## Right-to-left
Icons and titles on the right; the Next chevron on the left, pointing left. Arabic: "قيمنا", "الأسئلة الشائعة", "الدعم", "سياسة الخصوصية", "شروط الاستخدام", "البروتوكولات", "استعادة المشتريات".
