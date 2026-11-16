# UpdateRequiredScreen

A blocking screen on iPhone and iPad when the app version is too old to use. The only action is Update, which opens the App Store page.

Source: `UI/UpdateRequiredScreen.swift`.

## Layout (screen width `lw`)
- Ground: `GradientBackground` (gradient only).
- Centred group (gap 20, side padding 32), with equal flexible space above and below:
  - `assets/Logos/App-Logo.png`, 161 × 60, aspect fit.
  - Title `ALERTS.UPDATE_ALERT.TITLE` "Update Required": `H6`, `--text-primary`, centred.
  - Text `ALERTS.UPDATE_ALERT.DESCRIPTION`: `Body1`, white at 82 % (`Theme.text.primary.opacity(0.82)`, no token), centred.
- `RadialGradientButton` large, green: `ALERTS.UPDATE_ALERT.BUTTON` "Update". Bottom padding `max(bottom inset, 16) + 24` (58 on a notched iPhone).

## States
One state. The button press opens the App Store; the screen stays.

## Right-to-left
Everything is centred, so nothing moves. Arabic: "يتطلب تحديثاً", "نسخة التطبيق الخاصة بك قديمة. يرجى التحديث للمتابعة.", "تحديث". The Arabic text wraps to two lines.

## Notes
- Vertical positions: this component preview (390 × 844) uses top inset 0. On the device the content starts below the system top inset, and the bottom comes from the window's safe area. The screen cards in the Screens group show this (47 pt top inset on a 390 × 844 iPhone, or the system sheet edge) and are checked against screenshots where one exists.
