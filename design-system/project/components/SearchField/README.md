# SearchField

The Mac location search field, above the location list.

Source: `native/Design/SearchField.swift` (`SearchField`).

## Anatomy
- `HStack` spacing 8: SF Symbol `magnifyingglass` in `--mediumGray` (system size), then a plain `TextField` in `body` (Red Hat Display 15).
- Padding 12 horizontal, 10 vertical.
- `RoundedRectangle(12, .continuous)`: fill `--surface` (white 6 %), 1 pt `--hairline` border.
- Placeholder: `servers.search` ("Search locations" / "ابحث عن موقع"). macOS draws the placeholder colour; the preview uses white 25 % as a stand-in.
- Autocorrection off. Cmd+F focuses search (`shortcut.search`).

## Where
- Main window sidebar: 12 padding on all sides.
- Menu bar panel picker, under the "All locations…" header.

## States
Empty (placeholder), with text. A search with no match shows "No location found" in the list (see MacServerList).

## Right-to-left
The magnifier moves to the right side, the text is right-aligned.
