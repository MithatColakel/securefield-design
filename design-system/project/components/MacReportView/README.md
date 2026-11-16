# MacReportView

The Mac "Report a problem" sheet.

Source: `native/Design/FlowViews.swift` (`ReportView`). Shown by `MacRootView` as the `.report` sheet, 480 × 640, background `--sheetBackground` #0E1621.

## Layout (`VStack` leading, spacing 16, padding 24, max width 520)
1. `report.title` in `headline` (NAMU-1850 22).
2. `report.explain` in `body`, `--lightGray`.
3. `report.kind` in `bodyBold`.
4. Kind list in a CardBackground (radius 16): five rows, `body` text + SF Symbol `largecircle.fill.circle` `--lightGreen` (selected) or `circle` steel; padding 10 vertical, 16 horizontal; a Divider overlaid `--hairline` between rows. Kinds: Unable to connect, Connected but no internet, Low speed connection, Premium membership issue, Other.
5. `report.details` in `bodyBold`.
6. Text editor: `body`, padding 8, height 84, CardBackground radius 12.
7. Toggle "Attach connection details" (`body`) with the note (`caption`, `--mediumGray`), tint `--lightGreen`. On by default.
8. Buttons (`HStack` 12): Cancel (OutlineButtonStyle, Esc), Send (PrimaryButtonStyle height 44, Return; a small spinner while sending).
9. Result: `caption`, `--lightYellow`: "Thank you. Your report was sent." (the sheet closes after 1.2 s) or "The report could not be sent. Try again later."

## Fit
The sheet has no scroll view. In the Arabic render, with the result line, the content is about 20 px taller than 640. The render uses fallback fonts. The Mac screenshots (EN, AR) show the fixed 480 × 640 sheet with nothing cut off.

## Right-to-left
The column mirrors; radio marks move to the left.

## Stand-ins
The Toggle is the default `Toggle` with the tint `lightGreen`. macOS draws it as a checkbox; the preview draws a checkbox stand-in. In the screenshots macOS draws it grey with a white tick. Radio symbols are stand-ins.
