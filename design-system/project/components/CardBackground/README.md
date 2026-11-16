# CardBackground

The Mac card surface: a translucent white fill with a hairline border. Applied with `.brandCard(radius:)`.

Source: `native/Design/Brand.swift` (`CardBackground`, `brandCard`).

## Anatomy
- Fill: `RoundedRectangle(cornerRadius: radius, style: .continuous)` in `--surface` (white 6 %).
- Border: 1 pt `strokeBorder` in `--hairline` (white 12 %), inside the shape.
- Radius: `--radius-card` 16 by default; 12 (`--radius-field`) for the Report text field.
- No padding of its own: the content sets it (16 = `--space-l` in all uses).
- `.continuous` corners are Apple's squircle. CSS `border-radius` draws a circular corner, slightly different.

## Where
- PermissionView steps card (radius 16).
- ReportView kind list (radius 16) and details field (radius 12).
- `InfoTile` uses it too, but InfoTile is not on any screen on `main@00e1b7b`.
- The same look, written out by hand with radius 12, is used by the panel location row, SearchField and (yellow-tinted) the premium strip / card.
