# Logos

Brand marks and the app icon, copied with no change from `native/SecureFieldApp/SecureFieldApp/Resources/Assets.xcassets/`. Never redraw them.

| File | Size | Used in |
|---|---|---|
| `App-Logo.png` | 431 × 160 | Word-mark. iPhone main header (`UI/MainScreen.swift`), UpdateRequired screen. Mac: sidebar (height 22), menu bar panel header (22), paywall (34), welcome (64). |
| `Splash.png` | 1500 × 3248 | iPhone/iPad splash background (`UI/SplashScreen.swift`). |
| `Privacy-Logo.png` | 496 × 496 | PrivacyConsent screen (`UI/PrivacyConsentScreen.swift`). |
| `Premium.png` | 1116 × 1116 | Crown art: PremiumScreen (`:77`), Settings premium card (`UI/SettingsScreen.swift:135`), premium pop-up (`UI/PremiumPopUpScreen.swift:66`), iPad settings sidebar (48 × 48, `UI/WideLayout.swift:88`), iPad premium rows (16 × 16, `UI/WideServerList.swift:85`). |
| `AppIcon-1024.png` | 1024 × 1024, no alpha | iOS app icon (`AppIcon.appiconset`, `platform: ios`). |

## Mac app icon
The same `AppIcon.appiconset` holds the Mac sizes (`idiom: mac`). They are separate files with their own pixels (the Mac 1024 is not the iOS 1024: it has alpha).

| File | px | Slots in `Contents.json` |
|---|---|---|
| `AppIcon-mac-16.png` | 16 | 16 pt @1x |
| `AppIcon-mac-32.png` | 32 | 16 pt @2x, 32 pt @1x |
| `AppIcon-mac-64.png` | 64 | 32 pt @2x |
| `AppIcon-mac-128.png` | 128 | 128 pt @1x |
| `AppIcon-mac-256.png` | 256 | 128 pt @2x, 256 pt @1x |
| `AppIcon-mac-512.png` | 512 | 256 pt @2x, 512 pt @1x |
| `AppIcon-mac-1024.png` | 1024 | 512 pt @2x |

The Mac menu bar item is not a file: it is the SF Symbol `shield` (template, idle) or `checkmark.shield.fill` (lightGreen when connected, lightYellow while connecting), 15 pt semibold (`native/MacApp/MacPanel.swift:361`). See MacPanel.
