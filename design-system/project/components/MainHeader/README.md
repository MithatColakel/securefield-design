# MainHeader

The top bar of the iPhone and iPad main screen: premium crown, logo, report and settings.

Source: `UI/MainScreen.swift` (`MainHeader`).

## Anatomy
- Three parts in one row: leading slot 80 × 40, flexible space, `assets/Logos/App-Logo.png` at 107.55 × 40, flexible space, trailing slot 80 × 40.
- Leading slot: `icons/Premium` 24 × 24 (original colours) for a free user; empty for a premium user.
- Trailing slot, two 40-wide halves: `icons/Warning` 20 × 20 tinted `--icon-primary` (opens Report), then `icons/Settings` 24 × 24 (original colours, #D1DCEA).

## Props
`isPremium`, `onPremium`, `onReport`, `onSettings`.

## Right-to-left
The row follows the layout direction: in Arabic the crown is on the right and report / settings on the left. No icon mirrors.
