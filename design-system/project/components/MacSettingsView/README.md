# MacSettingsView

The Mac Settings window: one page with four sections, no tabs. Opened with Cmd+, (app menu "Settings…"), the panel's gear and the main window toolbar.

Source: `native/MacApp/MacRootView.swift` (`MacSettingsView`), sections in `native/Design/SettingsViews.swift`. Scene: `Window("Settings", id: "settings")`, `.contentSize` (`SecureFieldMacApp.swift:68`).

## Frame
460 × 700, `Form` with `.formStyle(.grouped)`, scroll background hidden, background `--sheetBackground` #0E1621. The form scrolls: at 700 the end of Support is below the fold.

## Sections
1. **General**: Toggle "Open at login" (Mac only); Toggle "Connect when the app opens"; "Appearance" with the value "Dark" in `--lightGray` (one theme only).
2. **Protocols**: one row per protocol (Smart, Securefield Shield, Wireguard, Hysteria2, OpenVPN). Smart has the green Badge "Recommended" (white text on `[lightGreen, darkGreen]`). The chosen row has `checkmark` in `--lightGreen`. Footer: `settings.protocols.note` in `caption`, `--mediumGray`.
3. **Subscription**:
   - Premium: `crown.fill` `--lightYellow`, plan name `bodyBold` (`settings.planYearly` …), detail `caption` `--lightGray` ("Renews …", "Ends …" or "Free trial · ends …"); "Manage subscription" opens the App Store subscriptions page.
   - Not premium: a row with `crown.fill`, "Get Premium Now" `bodyBold` `--lightYellow`, `chevron.forward` `--mediumGray` (caption size). Opens the paywall in the main window.
   - "Restore purchases"; the answer under it in `caption`, `--lightGray`.
4. **Support**: FAQ, Report a problem, Privacy Policy, Terms of Use (each opens a sheet in the main window), Rate us (App Store review page), Version `x.y (build)` in `--lightGray`.

Texts without a style use the system font of the form (13 pt on macOS); only the rows with `.brand(...)` use Red Hat Display.

## Right-to-left
The form mirrors. The version number stays left-to-right in the preview. The chevron: here `chevron.forward` has no `flipsForRightToLeftLayoutDirection`, so it turns once, as the system does.

## Stand-ins
macOS draws the grouped sections, toggles (switches), buttons and the title bar. The preview draws simple stand-ins with the system font. Toggle tint: the app sets `.tint(Brand.lightGreen)` in `brandEnvironment`. Plan date and version are samples. Check against a Mac screenshot.
