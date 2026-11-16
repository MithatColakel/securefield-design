# MacDocumentSheet

The Mac help and legal sheet: the FAQ with its list of documents, or one document (Privacy Policy, Terms of Use). The pages are the same bundled `.html` files the iPhone shows.

Source: `native/MacApp/MacDocument.swift` (`MacDocument`, `MacDocumentSheet`). Shown by `MacRootView` (`.doc` sheet).

## Layout
- Size: 820 × 560 with the list (FAQ), 620 × 560 for one document. Background `--sheetBackground` #0E1621.
- Header, padding 16: title in `headline` (NAMU-1850 22): "FAQ" (`FREQUENTLY_ASKED_QUESTIONS.HEADER.TITLE`) or the document title; spacer; close `xmark.circle.fill` 20, steel (`--auroMetalGray`), Esc.
- Divider overlaid `--hairline`.
- FAQ: a system `List` 220 wide (Payment & Subscription, Can't connect, Can't access Web/App, Profile/Installation, How Securefield works?, Other Issues), a divider, then the page.
- The page: `WKWebView` with a transparent background, loading `Resources/Documents/<name>.<lang>.html`, else `<name>.html`. Links open in the browser.
- Closing a document opened from the paywall goes back to the paywall.

## Arabic
- The sheet mirrors: the list moves to the right, the close button to the left.
- **Missing Arabic pages:** there is no `payment.ar.html`, `cant-access.ar.html`, `profile.ar.html` or `how-works.ar.html`. In Arabic the FAQ opens on the English Payment page, and 4 of the 6 FAQ pages are English. The `.ar` legal pages exist, but their text is damaged.

## Stand-ins
The list and its selection colour are drawn by macOS; the preview uses a stand-in. The page content is the document file itself and is not redrawn: the preview shows where it goes.
