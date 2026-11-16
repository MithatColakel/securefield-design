# GradientBorderButton

The secondary button: a GradientBorderCard (radius 24) with a Red Hat Display label and an optional icon. On `main` it is used once, for "Watch Ads" on the advertisement screen, above the green "Get Premium" RadialGradientButton.

Source: `UI/GradientBorderButton.swift`.

## Anatomy
- Surface: GradientBorderCard, radius 24 (`--radius-button`): `--background-secondary` fill, `--gradient-border` 1px edge, inner highlight.
- Size: full container width (the advertisement screen sets 83 %), aspect 4.64, max width 460 on iPad.
- Content: HStack spacing 8: optional 20 × 20 icon (original colours), label Red Hat Display Regular 16, `--text-primary`. Content has 5 pt top padding.

## Props
`title`, `icon` (asset name, optional), `isLoading`, `action`.

## States
- Default; pressed (scale 0.97, opacity 0.85).
- Loading: a white circular spinner replaces the content; the button is disabled. Change animates ease-in-out 0.2 s. The preview draws a static stand-in for the system spinner.

## Right-to-left
The icon sits on the leading side, so it is to the right of the label in Arabic. `icons/Play` does not mirror.
