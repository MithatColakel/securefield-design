# MacFirstLaunch

The Mac first-launch pages in the main window: Welcome, the VPN permission step, and the state after the user refused the permission.

Source: `native/Design/FlowViews.swift` (`WelcomeView`, `PermissionView`), flow in `native/MacApp/MacRootView.swift` (`Flow`: welcome → permission → main; denied).

## Frame
The window is 480 × 640 for these pages. Content is centred on BrandBackground with the map. `VStack` spacing 24, padding 32, max width 520.

## WelcomeView
- `App-Logo.png` height 64.
- `welcome.title` in `title` (NAMU-1850 28), centred.
- Three points (`VStack` 12, leading): `checkmark.circle.fill` `--lightGreen` + `body`.
- "Accept and continue": PrimaryButtonStyle, max width 320, Return.

## PermissionView
- Icon: 96 circle, blue #008FF5 at 18 % (denied: red #E94E30 at 18 %); SF Symbol 44 pt `lock.shield.fill` with `connectGradient` top → bottom (denied: `exclamationmark.shield.fill`, [lightRed, red]).
- Title `title`; body `body` `--lightGray`; both centred.
- Not denied: a steps card (CardBackground, padding 16) with three rows (`HStack` 12): number `bodyBold` white in a 26 circle `--darkBlue`, then `body`. Steps 1–2 have Mac texts (`perm.step1.mac`, `perm.step2.mac`).
- Button: PrimaryButtonStyle, max 320: "Continue", or "Try again" when denied.
- Denied, Mac only: "Open System Settings" in `body`, `--lightGreen` (plain button). It opens the VPN pane of System Settings.

## Right-to-left
All rows mirror. The preview shows Arabic for all three pages.

## Stand-ins
The shield symbols are simple stand-ins (one colour, not the gradient). The check symbol too. Vertical positions are checked against the Mac screenshots (see the Mac page of the screen canvas). In Arabic the step numbers are Arabic-Indic digits (١ ٢ ٣).
