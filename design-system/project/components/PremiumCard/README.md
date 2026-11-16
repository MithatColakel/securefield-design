# PremiumCard

One subscription plan on the app's own paywall (`PremiumScreen`) and the premium pop-up. Includes `PremiumCardTag`, the badge on its top edge.

Source: `UI/PremiumScreen.swift` (`PremiumCard`, `PremiumCardTag`).

## Anatomy (card width `w`; values at w 366 = layout width 390 − 2 × 12)
- `GradientBorderCard`, radius 24 (`--radius-button`). Aspect ratio 4.76: height `w / 4.76` (76.9). Horizontal padding 12 outside the card. On a tablet the card is at most 505 wide.
- Padding as fractions of `w`: leading `w × 0.08` (29.3), trailing `w × 0.055` (20.1), top `w × 0.045` (16.5), bottom `w × 0.034` (12.4).
- Leading column:
  - Plan name, `Subtitle1`, `--text-primary`: "Yearly" / "Monthly" / "Weekly" (`PRODUCTS.YEARLY` …).
  - At least 4 of space.
  - "Then {{price}} / {{period}}" (`PREMIUM.PRIMARY_PRICE`), `Caption`, `--text-tertiary`. Period: "Year" / "Month" / "Week".
- At least 8 of space.
- Trailing group, gap `w × 0.075`:
  - Secondary price, `Body1`, `--text-quaternary` (lightYellow), one line, shrinks to 75 %. "{{price}} / {{period}}" (`PREMIUM.SECONDARY_PRICE`); with a free trial "{{duration}} free trial" (`PREMIUM.SECONDARY_PRICE_TRIAL`) replaces the price.
  - `RadioButton`, variant `grayOrange`, diameter `(w / 4.76 − w × 0.079) × 0.64` (30.7).
- The whole card is the tap target.

## PremiumCardTag
- Shows when the product has a badge: "Best offer" (`PREMIUM.BADGE_BEST`) or "Most Popular" (`PREMIUM.BADGE_POPULAR`).
- Top-trailing. Height `card height × 0.347` (26.7). Offset `−w × 0.058` in x (toward the leading side) and `−height × 0.1735` in y, so it straddles the top edge.
- Text: Red Hat Display Regular 12 (15.6 on a tablet), `--text-primary`, one line. Padding 12 horizontal.
- Capsule fill `--gradient-controlTagBlue`, 1 pt border white at 10 % (`--border-primary` at 10 %).

## States
- Not selected: `gradient` border, radio off.
- Selected: border `--gradient-controlOrange` (variant `radialOrange`), radio on.
- With and without a tag; with a free trial.

## Right-to-left
Plan name and prices on the right; the radio on the left. The tag sits top-left (trailing). Arabic: "سنوي", "ثم {{price}} / سنة", "أفضل عرض", "تجربة مجانية لمدة {{duration}}".

## Preview notes
Prices and the trial length are sample values. Real prices come from the App Store at run time.
