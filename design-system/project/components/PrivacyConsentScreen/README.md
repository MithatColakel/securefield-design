# PrivacyConsentScreen

The first-run privacy screen on iPhone and iPad. It explains what the app collects. "Accept and continue" asks for tracking permission (App Tracking Transparency) and goes on.

Source: `UI/PrivacyConsentScreen.swift`, `UI/ScrollEdgeFade.swift` (`EdgeFadingScrollView`).

## Layout (screen `w` × `h`, bottom inset `b` = max(safe area, 16))
- Ground: `GradientBackground` (gradient only). `available = h − b`.
- Top band: height `available × 4.75 / 5.75`, top padding 14, centred column, gap 20:
  - `assets/Logos/Privacy-Logo.png`, square, `w × 0.27` (iPad `w × 0.2`).
  - Title `PRIVACY_POLICY.TITLE`: `H6`, centred, side padding 24.
  - Text box: width `w × 0.88`, fills the rest. Radius 20. Fill white 4.5 %, stroke 1 white 9 % (literals, no token). Scrolls; padding 18 / 18, top 18, bottom 28; paragraphs gap 14.
  - Paragraphs `PRIVACY_POLICY.CONTENT.DESC_1`…`DESC_4`: Red Hat Display Regular 13.5, line height 20, white 82 %. Not a named style.
  - Last paragraph `DESC_5`: same style in `--text-primary`. "Terms of Use" and "Privacy Policy" are links in `--text-secondary` (lightGreen); they open the document sheet.
  - Edge fade: the scroll view fades its edges by the hidden content, up to 48. At the top of the text only the bottom edge fades.
- Button band: height `available / 5.75`, `RadialGradientButton` large, green, centred: `PRIVACY_POLICY.BUTTON` "Accept and continue".
- The top padding 14 is outside the two bands, so the bands plus padding are 14 taller than `available`; the button band sits 14 lower. The preview copies this. **To confirm** against a device screenshot.

## States
- Default.
- After the press: the button ignores further taps while the tracking prompt is up.
- A link opens `DocumentScreen` as a sheet.

## Right-to-left
Paragraphs are leading-aligned, so in Arabic they align right. Arabic title "خصوصيتك هي أولويتنا القصوى" wraps to two lines. Button "قبول ومتابعة". The Arabic text fits without scrolling at 390 × 844; the English text scrolls.

## Notes
- Vertical positions: this component preview (390 × 844) uses top inset 0. On the device the content starts below the system top inset, and the bottom comes from the window's safe area. The screen cards in the Screens group show this (47 pt top inset on a 390 × 844 iPhone, or the system sheet edge) and are checked against screenshots where one exists.
