# MainTimerView

The free user's remaining free time on the iPhone and iPad main screen, with an "Add" button that opens the advertisement flow to earn more time.

Source: `UI/MainTimerView.swift`; placed in `UI/MainScreen.swift`.

## Use
- Free users only. Premium users never see it.
- It is pinned, not stacked: `padding(.top, phone × 0.07)` (27.3 at lw 390) inside the connect area, so the Connect button stays in the same place with or without the timer.
- On iPad the `phone` width is the main column's phone-sized width, not the window.

## Anatomy (layout width `lw`)
- Column, gap 10, centred, max width `lw × 0.5` (195 at lw 390). The title wraps inside it.
- Title: `MAIN.TIMER_VIEW.TITLE` "Your free gift expires in {{timer}}", `Subtitle1`, `--text-primary`, centred. The timer is `HH:MM:SS`, two digits each.
- Add button: capsule, height 30, padding 0 / 10, stroke 1 `--border-quaternary` (lightGreen), no fill.
  - `assets/Icons/Plus.svg` 9 × 9, gap 2.
  - `MAIN.TIMER_VIEW.BUTTON` "Add", upper-cased, `Amiko2`, `--text-secondary` (lightGreen), padding leading 1, top 2.

## States
- Running: the timer counts down once a second.
- Owed: the first free minutes of a new install show without counting down; they start at the first connection.
- Expired: `00:00:00`. It never shows a negative time.
- Add pressed: plain button press, then the advertisement screen.

## Right-to-left
The column is centred, so only the line order changes. The title reads right to left: "تنتهي هديتك المجانية بعد 00:29:41". The digits stay `HH:MM:SS` left to right (normal Unicode bidi for ASCII digits). The button reads "إضافة" with the plus on the right. Upper-casing has no effect on Arabic.

## Notes
- The runner has no SF fonts. Take SF sizes from code.
- The timer values in the preview are samples.
