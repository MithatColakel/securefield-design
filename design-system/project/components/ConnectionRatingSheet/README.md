# ConnectionRatingSheet

"How was your connection?" A bottom sheet on iPhone and iPad after a session ends. Five stars. A low rating (1–3) also asks what went wrong. Closing is always free and sends nothing.

Source: `UI/ConnectionRatingSheet.swift` (`ConnectionRatingSheet`, `StarRating`, `ReasonOption`). Shown by `UI/MainScreen.swift` as an overlay (not a system sheet).

## When it shows
After a session ends. Not when the app reconnects to a new server, not while a connect runs, and not when the session ended for a purchase.

## Layout (window `W × H`)
- Dim: black at 55 % (literal, not `--background-quaternary`), whole screen. A tap on it closes the sheet.
- Sheet: full width, anchored to the bottom, safe area ignored. Top corners 30, bottom corners square. Max height `H × 0.85`; otherwise it fits its content.
  - Fill: `--gradient-background` (top-leading to bottom-trailing).
  - Top edge: stroke 1 white at 10 % and an inset highlight (white 25 %, 2 wide, blur 2, offset 1, 1). Both fade out over the top 30. No tokens.
- Header (also the drag area): column, gap 14, padding top 12, sides 24.
  - Handle: capsule 44 × 4, white at 35 %.
  - Title `CONNECTION_RATING.TITLE` "How was your connection?": `H6`, `--text-primary`, centred.
  - Subtitle `CONNECTION_RATING.SUBTITLE`: `Body1`, `--text-tertiary`, centred, extra side padding 16.
  - `StarRating`: 5 stars, size 40, gap 8.
- Reasons (only for 1–3 stars, and not after a timer cut): column, leading, gap 10, padding sides 24, top 16.
  - Title `CONNECTION_RATING.REASONS_TITLE` "What went wrong?": `Subtitle1`, leading.
  - Seven `ReasonOption` rows, gap 8, in an `EdgeFadingScrollView` (only this list scrolls): Slow speed, Frequent disconnects, Couldn't connect, Connected but no internet, Server problems, App problems, Other.
- Footer: column, gap 10, padding sides 24, top 16, bottom `bottom inset + 16`.
  - `RadialGradientButton` large, green, `CONNECTION_RATING.SUBMIT` "Send". Disabled (opacity 0.45) until a star is set.
  - "Not now" `CONNECTION_RATING.SKIP`: `Body1`, `--text-tertiary`, padding top and bottom 6. A plain text button.

## StarRating
- Each star: SF Symbols `star.fill` with `star` over it, both at `size × size` (40 here; the type default is 46 / gap 10, not used).
- Set: fill and outline `--text-quaternary` (lightYellow #FAC762).
- Not set: fill white at 6 %, outline white at 35 % (no tokens).
- Tap: light haptic; the fill changes with ease-out 0.15 s. Tapping star N sets N.

## ReasonOption
A multi-select row. Radius 14, padding 12 top and bottom, 18 sides. Label `Body1`, leading, then a 22 × 22 check box (gap 12).
| | Not selected | Selected |
|---|---|---|
| Row fill | white 4 % | lightGreen 12 % |
| Row stroke (1) | white 14 % | `--border-quaternary` (lightGreen) |
| Box stroke (1.5, radius 6) | white 35 % | `--border-quaternary` |
| Check | — | SF `checkmark`, 12 bold, `--border-quaternary` |

## States
- No stars: Send is disabled.
- 1–3 stars: the reasons show (fade 0.2 s). Setting 4 or 5 stars clears the chosen reasons.
- 4–5 stars: no reasons. 5 stars also asks for an App Store review on the next app open (not here).
- Ended by the free-time timer: title `CONNECTION_RATING.TIMER_TITLE` "Your free time ran out", subtitle `CONNECTION_RATING.TIMER_SUBTITLE`. No reasons at any rating. No review prompt.
- Sent: the content changes to the handle, an SF `checkmark.circle.fill` 52 × 52 in `--text-secondary`, and `CONNECTION_RATING.SENT` "Feedback successfully sent" (`Subtitle1`, centred). Padding: 40 above and below the group, top 12, bottom `inset + 16`. The sheet closes by itself after 1.2 s.
- Entering: spring up from the bottom (response 0.4, damping 0.9), the dim fades in. Leaving: ease-in 0.22 s down.
- Drag down: the sheet follows the finger; past 110 or a fast fling it closes, otherwise it springs back.

## iPad
- Type scales ×1.3 (`H6` 28.6 / 31.5, `Body1` 19.5 / 27.3, `Subtitle1` 22.1 / 24.8, Send label 22.1). Star size, handle, boxes and paddings do not scale.
- The sheet is the full window width. The Send width follows the layout width: `min(window width, 560) × 0.83` (to confirm that the overlay gets this layout width). The preview uses 560.

## Right-to-left
- The reasons title and labels are right-aligned; the check box is on the left.
- Stars: star 1 is on the right in Arabic (normal SwiftUI mirroring of the row). **To confirm.**
- Arabic: "كيف كان اتصالك؟", "ملاحظاتك تساعدنا على تحسين تجربتك.", "ما الخطأ الذي حدث؟", "إرسال", "ليس الآن".

## Notes
- **Vertical positions to confirm.** The preview (390 × 844) uses bottom inset 34. The positions are checked against device screenshots.
- SF Symbols (`star`, `star.fill`, `checkmark`, `checkmark.circle.fill`) are not in the repo. The preview draws simple stand-ins.
- The main screen behind the dim is drawn as `GradientBackground` with the world map only.
