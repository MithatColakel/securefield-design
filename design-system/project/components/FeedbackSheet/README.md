# FeedbackSheet

"Are you satisfied with our service?" A card over the dimmed screen on iPhone and iPad. "Yes" opens the App Store review prompt. "No" opens an email to support.

Source: `UI/FeedbackSheet.swift`. Shown by `UI/MainScreen.swift` as an overlay (not a system sheet).

## When it shows
- It replaces a Connect press: the press does not connect.
- Free users: on Connect press 10, 30, 50, … (`(count + 10) % 20 == 0`).
- Premium users: on press 10, then every 50th press (`count == 10 || count % 50 == 0`).
- Source: `shouldPromptForFeedback` in `SecureFieldKit`.

## Layout (window `W × H`)
- Dim: `--background-quaternary` (bgBlack80) over the whole screen, safe area ignored. A tap on it closes the card.
- Card: width `min(W × 0.9, 520)`, height `H × 0.5` (351 × 422 on a 390 × 844 iPhone; 520 × 590 on an 820 × 1180 iPad). Radius 30.
  - Fill: `--feedbackField` (#82B3F2 at 16 %) over the system `.ultraThinMaterial` blur. Stroke 1, white at 25 % (no token).
- Close row: the close button at the trailing end, 56 × 56 hit area. Icon `assets/Icons/Close.svg` 24 × 24, drawn as a template in `--icon-secondary` (darkGray #3F4751). The file's own colour is not used.
- Content: column, gap 16, padding sides 24:
  - `assets/Images/Heart-Rate.svg`, height 96, aspect fit.
  - Title `FEEDBACK.TITLE` "Are you satisfied with our service?": `H5`, `--text-primary`, centred.
  - Text `FEEDBACK.TEXT`: `Body1`, `--text-primary`, centred, max 3 lines.
- Flexible space, min 16.
- Buttons: row, gap 12, padding sides 24, bottom 24. Both are height 52, radius 16, and share the width equally.
  - "No" (`FEEDBACK.BUTTON_2`), first: NAMU-1850 17, `--text-primary`; fill white at 8 %, stroke 1 white at 22 % (no tokens). It is the app's secondary button shape and is used only here.
  - "Yes" (`FEEDBACK.BUTTON_1`): `RadialGradientButton` `fill(height 52, cornerRadius 16)`, green, label 17.
  - Both labels are moved down to centre the capitals (`capCentringOffset`), as in RadialGradientButton.

## iPad
Type scales ×1.3: `H5` 36.4 / 40, `Body1` 19.5 / 27.3, button labels 22.1. The card, the icon, the image, the button height and the paddings do not scale.

## States
- Entering: the dim fades in; the card fades in and grows from 0.94 (ease-out 0.3 s).
- Shown: as above.
- Leaving (close, dim tap, Yes or No): the choice runs first, then the card fades out (ease-in 0.2 s). A second tap does nothing.
- Pressed: both buttons use `PressableButtonStyle` (scale 0.97, `--opacity-pressed`).

## Right-to-left
- The close button moves to the top-left.
- "No" stays first, so it is on the right. "Yes" is on the left.
- The heart image does not mirror (an image asset, no mirroring set).
- Arabic: "هل أنت راضٍ عن خدمتنا؟", "رأيك مهم بالنسبة لنا. هل أنت راضٍ عن جودة الخدمة؟", "لا", "نعم".

## Notes
- **Vertical positions to confirm.** The card is centred in the full window in the preview. The positions are checked against device screenshots.
- The preview draws the dim over `GradientBackground` with the world map only. In the app the whole main screen is behind it, and the material blurs it. The blur in the preview (`backdrop-filter`) is an approximation of `.ultraThinMaterial`.
- The close icon (`--icon-secondary`, darkGray) looks low in contrast on the card. The ratio is in the README brand book (Contrast).
