# Advertisement

The "watch ads" screen on iPhone and iPad. A free user watches 3 ads to earn 15 minutes of free time, or chooses Premium. Opened from the Add button of `MainTimerView`. Includes `AdvertisementTopView` and `AdvertisementStepIndicator`.

Source: `UI/AdvertisementScreen.swift`. Constants `REWARD_MAX_ADS = 3`, `REWARD_DURATION_MINUTES = 15` in `Ads/AdReward.swift`.

## Layout (content height `h`, screen width `lw`)
- Ground: `GradientBackground` (gradient only).
- **Top view**, height `h × 0.38`: `assets/Images/Advertisement-Background.png`, fill, aligned to the bottom, clipped. Close button over it at top-leading, padding 12: 44 × 44 tap area, 34 × 34 circle black 35 % (literal, no token), `icons/Close` 16 × 16 tinted `--icon-primary`. Pressable style.
- **Middle**, height `h × 0.31`, equal flexible gaps between:
  - Title `ADVERTISEMENT.TITLE`: `Amiko3` (Red Hat Display 25 / 27.5, tracking −0.5), centred, max width `screen width × 0.874`.
  - Text `ADVERTISEMENT.DETAIL` (3 ads, 15 minutes): `Amiko4` (Red Hat Display 14 / 19.6), centred, max width `screen width × 0.829`.
  - Step indicator: width `min(lw, 560) × 0.538`, 3 `RadioButton`s (green), diameter `width × 0.075`, spread evenly. Watched: selected, scale 1.1. Not yet: off, scale 0.8, opacity 0.6. Animated 0.3 s.
- **Bottom**, height `h × 0.29`, content at the bottom, bottom padding `max(bottom inset, 16)`:
  - Gap 20 between `GradientBorderButton` ("Watch Ads", `icons/Play`, width `lw × 0.83`) and `RadialGradientButton` large green ("Get Premium").
  - Gap 3, then the price line `ADVERTISEMENT.SUB` "{{price}} / {{period}}. Cancel anytime.": `Caption`, `--text-secondary`, one line, scales down to 75 %. A blank line while the price loads.
  - Gap 3, `LegalFooter`.

## States
- 0, 1 or 2 ads watched (step indicator).
- Ad loading or playing: Watch Ads shows a spinner and is disabled.
- After the third ad the reward is granted and the screen closes.
- Get Premium opens the paywall.

## Right-to-left
The close button moves to the top-right. The step indicator mirrors: the first watched step is on the right. The Play icon stays before the label (leading side) and is not mirrored. Arabic: "شاهد الإعلانات للاتصال بـ Securefield", "شاهد الإعلانات", "احصل على المميز", "يمكنك الإلغاء في أي وقت".

## Notes
- Vertical positions: this component preview (390 × 844) uses top inset 0. On the device the content starts below the system top inset, and the bottom comes from the window's safe area. The screen cards in the Screens group show this (47 pt top inset on a 390 × 844 iPhone, or the system sheet edge) and are checked against screenshots where one exists.
- The price in the preview is a sample. The spinner is a static stand-in.
- The preview takes the content height as 844 (top inset 0, bottom inset 34), like the other screen previews. See the safe-area question in the hand-off.
