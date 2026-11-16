# GradientBorderCard

The panel that every list, card and sheet on iPhone and iPad sits in: a 20 % ice-blue fill with a lit edge that fades from the top-leading corner.

Source: `UI/GradientBorderCard.swift` (with `RowSeparator`).

## Anatomy
- Fill: `--background-secondary` (iceBlue, #82B3F2 at 20 %). No blur or material.
- Border: 1px, `--gradient-border` (white at 20 % to clear, top-leading to bottom-trailing).
- Inner highlight: the CSS original is `1px 1px 2px 0 #FFFFFF40 inset`. The app draws it as a 2 pt white @ 25 % stroke, blur 2, offset (1, 1), masked to fade out to the bottom-trailing corner. The preview uses the CSS inset shadow.
- Radius: `--radius-gradientCard` (28) by default. 24 (`--radius-button`) on GradientBorderButton and the premium cards.

## Props
- `cornerRadius` (default 28).
- `topCornersOnly`: only the top corners round. Use it for panels flush with the bottom edge (MainServerView).
- `variant`: `gradient` (default) or `radialOrange`.
- Content: any view.

## States
- `gradient`: the normal state everywhere.
- `radialOrange`: a SELECTION state, not a second look. A paywall plan card switches to it when it is the chosen plan. The border is `--gradient-controlOrange` (exact SVG radial geometry).

## RowSeparator
A 1px line in `--separator-secondary` (auroMetalGray #6D767D), 95.3 % of the card width, aligned to the trailing edge. So it starts under the label, not under the icon. In Arabic it sits flush right (preview uses `margin-inline-start:auto`).

## Do / don't
- Do use it for grouped rows (settings actions, protocols, report reasons).
- Don't add a coloured outline or a shadow under it. The lit edge is the only border.
