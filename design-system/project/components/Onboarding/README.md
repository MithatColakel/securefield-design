# Onboarding

The first-run carousel on iPhone and iPad: four slides, each with its own Lottie. The last slide is also the paywall: it shows the price line, the Close and Restore header, and its primary button buys the plan. Includes `OnboardingSlideView` and `Paginator`.

Source: `UI/OnboardingScreen.swift`. Lotties: `Resources/Lotties/Lock.json`, `Globe-and-pins.json`, `Speedometer.json`, `Shield.json`, copied to `assets/Lotties/`.

## Use
- Shown once, on first run. The remote `flow_onboarding` can replace it, with this screen as the fallback; that remote flow is off since 2026-09-26 (`FlowLibrary.onboardingUsesFlow`).
- Slides, in order (`ONBOARDING.CONTENT.<n>.TITLE` / `.SUB_TITLE`): 0 Lock "Surf the Web Privately", 1 Globe-and-pins "Access Global Content", 2 Speedometer "Fast & Stable Connection", 3 Shield "Connect now!".

## Layout (screen height `h`, width `w`, bottom inset `b` = max(safe area, 16); 34 on a notched iPhone)
- Background: `GradientBackground` (gradient only).
- `available = h − b`. Footer height `available / 5.75`; the pager band gets the rest.
- Pager band: horizontal paging scroll view, then `Paginator` with 12 bottom padding.
- Slide (`OnboardingSlideView`), two parts:
  - Top (fills, content centred, gap 8): `RestoreCloseHeader` ("Restore", `ONBOARDING.RESTORE_BUTTON`), then the Lottie, square, `w × 0.8` (iPad `w × 0.55`).
  - Copy block: min height `slide height × 0.32`, vertical padding `slide height × 0.05`, centred.
    - Title: NAMU-1850 32, line height 35.2, `--text-primary`. One size up from `H5`; not a named style.
    - Gap 28. Text: Red Hat Display Regular 17, line height 23.8, `--text-primary`, side padding `w × 0.12`.
    - Spacer, min 16. Price line: Red Hat Display Regular 14, `--text-tertiary`, centred.
  - iPad: all four font sizes and line heights × 1.3, rounded to 0.1 (`DeviceClass.scaleFont`): 41.6 / 45.8, 22.1 / 30.9, 18.2.
- Footer (gap 12, side padding 24, content at the bottom): `RadialGradientButton` (green), then (gap 8) "Auto-renewable subscription" (`ONBOARDING.AUTO_RENEWABLE`, `Caption`, `--text-tertiary`) and `LegalFooter`.

## Paginator
Row, gap 8. Dot 6 × 6 capsule, `--paginator-primary` (darkGray). The current dot stretches to 24 wide and uses `--paginator-secondary` (lightGreen). Animated 0.2 s ease-in-out.

## States
- Slides 0–2: button "Next" (`ONBOARDING.BUTTON_NEXT`); header and price line at opacity 0 (they keep their space).
- Last slide: header and price line fade in (0.25 s). Button "Continue" (`ONBOARDING.BUTTON_CONTINUE`) buys the plan.
- Last slide, plan loading: Continue stays live (it is off only while a purchase or restore is busy). A press waits for the plan (max 8 s) with a spinner in the button, then buys or shows "Try again". A small system spinner in `--text-tertiary` sits where the price will be.
- Last slide, load failed: the button reads "Try again" (`Strings.Premium.retryButton`).
- Busy (purchase or restore): `LoadingOverlay` over the whole screen.
- Price line, three forms: `ONBOARDING.SUBSCRIPTION_DETAIL` "Get started with just {{price}} per {{period}}"; `ONBOARDING.SUBSCRIPTION_TRIAL` "Start your {{trialPeriod}} free trial\nThen {{price}} per {{period}}"; `ONBOARDING.SUBSCRIPTION_WITH_PROMOTIONAL` "Start at {{offerprice}} / {{offerperiod}}\nThen {{price}} per {{period}}".
- Lottie: plays once when the slide shows, then holds the last frame. The preview shows the last frame.

## Right-to-left
Text is centred, so lines only change reading order. The header mirrors: Close on the right, "استعادة" on the left. The paginator and the paging mirror with the layout (normal SwiftUI mirroring): the first slide's dot is on the right. Arabic: "التالي", "متابعة", "اشتراك متجدد تلقائيًا". The longest Arabic text (slide 2) wraps to three lines and fits.

## Notes
- Vertical positions: this component preview (390 × 844) uses top inset 0. On the device the content starts below the system top inset, and the bottom comes from the window's safe area. The screen cards in the Screens group show this (47 pt top inset on a 390 × 844 iPhone, or the system sheet edge) and are checked against screenshots where one exists.
- Prices and the trial length in the preview are samples.
- The system spinner is a static stand-in.
- The preview loads the local copy of `lottie-web` 5.12.2 (`vendor/lottie-web-5.12.2/`). It needs no network. Over `file://` the browser blocks the Lottie files; open it over HTTP (the design page does).
