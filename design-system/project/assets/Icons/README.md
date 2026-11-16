# Icons

App icons, copied with no change from `native/SecureFieldApp/SecureFieldApp/Resources/Assets.xcassets/icons/`. iPhone and iPad only. The Mac app uses SF Symbols, which are not in the repo (see the Mac components).

Every icon has `template-rendering-intent: original` in its `Contents.json`. The app draws the file's own ink; a `foregroundStyle` in code does not recolour it. The ink of each file is in the table, because the design page shows icons through `<img>` (no `currentColor`).

| File | Ink (in the file) | Used in (on `main@00e1b7b`) |
|---|---|---|
| `Back.svg` | #D1DCEA (`lightGray`) | `UI/ServerListScreen.swift:103` BackTitleHeader. Mirrors in Arabic (`flipsForRightToLeftLayoutDirection`). Also the debug screen. |
| `Close.svg` | #D1DCEA | `UI/FeedbackSheet.swift:79`, `UI/AdvertisementScreen.swift:172`, `UI/PaywallChrome.swift:29` (RestoreCloseHeader). |
| `Done.svg` | #35DF91 (`lightGreen`) | Settings row Restore purchases (`UI/SettingsScreen.swift:113`); premium pop-up feature check (`UI/PremiumPopUpScreen.swift:250`). |
| `Down.svg` | `currentColor` | Server list header on iPhone (`UI/ServerListScreen.swift:37`), close arrow of the sheet. Does not mirror. The file has no fixed ink: with `original` rendering the shown colour is to confirm on a device. |
| `Faq.svg` | #35DF91 | Settings row FAQ (`UI/SettingsScreen.swift:107`). |
| `Heart.svg` | #35DF91 | Settings row Rate us (`:106`). |
| `Next.svg` | #D1DCEA | Settings row chevron (`UI/SettingsScreen.swift:245`) and FAQ document row (`UI/DocumentScreen.swift:327`). Both mirror in Arabic. |
| `Play.svg` | #FFFFFF | Advertisement play button (`UI/AdvertisementScreen.swift:85`). |
| `Plus.svg` | #35DF91 | Add-time pill in MainTimerView (`UI/MainTimerView.swift:33`). |
| `Premium.svg` | #FAC762 (`lightYellow`) | Main header premium button (`UI/MainScreen.swift:1226`). |
| `Privacy-Policy.svg` | #35DF91 | Settings row Privacy Policy (`:109`). |
| `Protection.svg` | #FAC762 | Premium feature line (`UI/PremiumPopUpScreen.swift:86`, `UI/SettingsScreen.swift:147`). |
| `Protocol.svg` | #35DF91 | Settings row Protocols (`:111`). |
| `Settings.svg` | #D1DCEA | Main header settings button (`UI/MainScreen.swift:1256`). |
| `Speed.svg` | #FAC762 | Premium feature line (`UI/PremiumPopUpScreen.swift:80`, `UI/SettingsScreen.swift:145`); also the debug-only network row (`:112`). |
| `Support.svg` | #35DF91 | Settings row Report a problem (`:108`). |
| `Terms.svg` | #35DF91 | Settings row Terms of Use (`:110`). |
| `Tick.svg` | #171D2E | Check inside the selected RadioButton with tick (`UI/ServerListScreen.swift:336`), 45 % of the radio. |
| `Warning.png` | full colour, 512 × 512 | Main header report button (`UI/MainScreen.swift:1246`). |
| `World.svg` | #FAC762 | Premium feature line (`UI/PremiumPopUpScreen.swift:83`, `UI/SettingsScreen.swift:146`). |

## In the repo, not used by code
`Connected.svg` (a white 32 × 32 rounded square), `Connection-Error.svg` (white) and `Language.svg` (#35DF91) are in the catalog, but no Swift code on `main@00e1b7b` loads them. They are kept as files so the set matches the repo.

## Contrast
Icons that carry meaning need 3:1 on their background. The ratios are in the README brand book (Contrast).
