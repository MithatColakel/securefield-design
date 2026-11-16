# LargeTitleBar

The iOS system navigation bar with a large title, on iPhone and iPad. The title starts large above the page and folds into the bar when the content scrolls under it. The app sets only the title font and colour and the one leading button. iOS draws everything else.

Source: `UI/LargeTitleBar.swift` (`largeTitleBar(_:exit:onExit:)`, `NavigationBarStyle`).

## Where it is used
- Settings (`SETTINGS.HEADER.TITLE`), Protocols (`PROTOCOLS.HEADER.TITLE`), FAQ (`FREQUENTLY_ASKED_QUESTIONS.HEADER.TITLE`), and every document (`DocumentScreen`).
- A document opened from a legal footer opens in a sheet (`DocumentSheet`) with the close button.
- These pages used `BackTitleHeader` before. `BackTitleHeader` is now used only on the server list (and a debug-only screen).

## What the app sets
- Large title: NAMU-1850 34 (`H4` size), white. If the title is wider than the bar at 34, it is set at the size that fits: `max(22, floor(34 × available width / needed width))`. 22 is the `H6` size. The available width is the bar width minus its layout margins (40 when the bar is not laid out yet).
- Folded title: NAMU-1850 17 (`Subtitle1` size), white.
- Tablet: all three sizes ×1.3 (44.2, 28.6 and 22.1).
- Leading button: SF Symbol `chevron.backward` (a pushed page, `PageExit.back`) or `xmark` (a page in its own sheet, `PageExit.close`), tinted `--icon-primary` (lightGray #D1DCEA). The system back button is hidden.
- The colour of the titles is `UIColor.white` (= `--white`).

## What iOS draws (not set by the app)
- Bar height, title position and margins, background, blur and the folding animation.
- From iOS 26: Liquid Glass. The button is a glass capsule and the content blurs away under the bar.
- Before iOS 26: the classic bar, clear while the title is large and blurred when content passes under it.

## States
- Large: at the top of the page.
- Folded: the page is scrolled; the title is centred in the bar.
- Hidden exit: a page shown inside the iPad settings window has no leading button (`hidesPageExit`).

## Right-to-left
The bar mirrors (system behaviour): the button is on the right and `chevron.backward` points right. The large title is right-aligned.

## Notes
- The preview draws a stand-in of the bar. The heights (44 bar + 52 large-title area), the 16 margin and the blur are approximate iOS values, not values from code. They are checked against device screenshots.
- SF Symbols are not in the repo. The preview draws simple stand-ins.
