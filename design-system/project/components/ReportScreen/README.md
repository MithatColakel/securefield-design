# ReportScreen

"Report a problem" on iPhone and iPad. A list of problems. Each row sends a diagnostic report and then runs the fix that helps most often. One filled button, "No problem to report", is pinned at the bottom.

Source: `UI/ReportScreen.swift` (`ReportScreen`, `ReportItem`, `ReportRow`). Opened from the Report icon in `MainHeader` (`UI/MainScreen.swift`).

## Where it shows
- iPhone: a system sheet.
- iPad, wide window: a form sheet (`FormSheetWhenWide`, `.presentationSizing(.form)`). The layout width is `WideLayout.formWidth` 540. The iPad settings window also shows it as its Support pane, at the same width.
- If a connection is still running, the app first asks "Still connecting — wait?" (`REPORT.STILL_CONNECTING.*`, a system alert: Wait / Report anyway).

## Layout (iPhone values; iPad scale in the table below)
- Ground: `GradientBackground` (gradient only).
- Header: title `REPORT.TITLE` "Report a problem", `Subtitle1`, `--text-primary`, centred. Padding top 25, sides 20, bottom 20.
- Close: the text glyph "✕" (U+2715), system font 20 bold, `--text-primary`, in a 75 × 75 hit area. It sits over the header at top-leading, moved 10 to the trailing side (`offset(x: 10)`). It is not the `Close.svg` icon.
- Scrolling column (`EdgeFadingScrollView`, fade up to 24 at an edge with hidden content): gap 12, padding sides 20, top 4, bottom 16.
  1. Explanation `REPORT.EXPLANATION`: its own style in code, Red Hat Display Regular 14 / line 19.6, letter spacing 0.04, `--text-tertiary`, centred. Padding sides 6, bottom 10. No token: it is `Body1` one point smaller, by product decision.
  2. Only while the tunnel is up: `REPORT.YOU_ARE_CONNECTED` "You are connected", `Body1`, `--text-primary`, centred, padding bottom 4.
  3. Reset row: `ReportRow`, icon `arrow.clockwise`, `REPORT.RESET_SERVERS` "Reset server list". It sends no report.
  4. Six problem rows (`ReportItem`), in this order: Unable to connect, Connected but no internet, Premium/free membership issue, Low speed connection, Ad reward not received, Can't watch ads.
- Pinned button: `ReportItem(.noProblem, isPrimary)` = `RadialGradientButton` `fill(height 56, cornerRadius 18)`, label 15 (not 17), "No problem to report". Padding sides 20, top 8, bottom 12, above the bottom safe area.

## ReportRow
`GradientBorderCard` with radius 18. Row: icon circle, title, chevron. Gap 14, padding sides 14, height 60.
- Icon circle: 34 × 34, fill `--text-secondary` at 12 % (lightGreen 12 %, no token). The SF Symbol is fitted in a 17 × 17 box, weight medium, `--text-secondary`, then scaled per row (`iconScale`).
- Title: `Body1`, `--text-primary`, leading, max 2 lines.
- Chevron: SF Symbol `chevron.forward`, system 13 semibold, `--text-tertiary` at 70 %.
- Pressed: `PressableButtonStyle` (scale 0.97, `--opacity-pressed`).

| Row | Key | SF Symbol | iconScale | Follow-up after the report |
|---|---|---|---|---|
| Reset server list | `REPORT.RESET_SERVERS` | `arrow.clockwise` | 1 | reloads servers; no report |
| Unable to connect | `REPORT.UNABLE_CONNECT` | `xmark.shield` | 1 | reloads servers |
| Connected but no internet | `REPORT.NO_INTERNET` | `wifi.exclamationmark` | 1.10 | reloads servers |
| Premium/free membership issue | `REPORT.MEMBERSHIP_ISSUE` | `crown` | 1.05 | restores purchases |
| Low speed connection | `REPORT.LOW_SPEED` | `tortoise` | 1.10 | reloads servers |
| Ad reward not received | `REPORT.AD_REWARD_NOT_RECEIVED` | `gift` | 1 | none |
| Can't watch ads | `REPORT.NO_REWARDED_ADS_AVAILABLE` | `play.slash` | 1.05 | none |
| No problem to report | `REPORT.NO_PROBLEM` | — (filled button) | — | none |

## iPad (tablet scale ×1.3)
| Value | iPhone | iPad |
|---|---|---|
| Row height | 60 | 72 (literal, not ×1.3) |
| Icon circle / glyph box | 34 / 17 | 44.2 / 22.1 |
| Chevron | 13 | 16.9 |
| Title (`Body1`) | 15 / 21 | 19.5 / 27.3 |
| Explanation | 14 / 19.6 | 18.2 / 25.5 |
| Header (`Subtitle1`) | 17 / 19.04 | 22.1 / 24.8 |
| Button label | 15 | 19.5 |
Paddings, gaps, the close glyph (20) and the button height (56) do not scale.

## States
- Idle: as above.
- Connected: the "You are connected" line shows above the reset row. The rows stay active.
- Submitting: `LoadingOverlay` (see PaywallChrome) covers the screen. A second press does nothing.
- Answer: a system alert. Reset or a connection row: "Connection Issue" / "Servers have been reset to fix the connection problem. Please try again." (Low speed has its own message). Membership: the restore answer. A failed send with no other answer: the error text. OK closes the sheet. "No problem" and the ad rows close the sheet at once.
- Too soon: a second report inside one minute shows `REPORT.TOO_SOON`. The sheet stays open.
- System alerts are drawn by iOS and are not in the preview.

## Right-to-left
- Rows mirror: icon circle on the right, chevron on the left. `chevron.forward` flips in Arabic (it is a "forward" symbol).
- The close glyph moves to the top-right (top-leading). The `offset(x: 10)` direction in Arabic is **to confirm**; the preview assumes it mirrors (10 towards the centre).
- At 390 the explanation is 5 lines in English and 4 in Arabic. No row title wraps, in either language, on iPhone or iPad.
- The row glyphs do not mirror, except where SF Symbols has its own right-to-left variant (to confirm for `tortoise` and `play.slash`; the preview does not mirror them).

## Notes
- **Vertical positions to confirm.** The preview (390 × 844) uses top inset 0 and bottom inset 34. The real sheet starts below the status bar with the system sheet's top gap. The positions are checked against device screenshots.
- SF Symbols are not in the repo. The preview draws simple stand-ins for the row glyphs and the chevron. Do not copy them; the app uses the system symbols.
- The runner has no SF fonts. The close glyph uses a fallback font in the preview. Take sizes from code.
