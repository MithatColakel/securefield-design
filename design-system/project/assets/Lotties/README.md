# Lotties

Lottie animations (JSON), copied with no change from `native/SecureFieldApp/SecureFieldApp/Resources/Lotties/`. iPhone and iPad only; the Mac app draws its own Connect orb.

| File | Source | Used in | Use |
|---|---|---|---|
| `TTC.json` | `Lotties/Connect/TTC.json` | `UI/MainConnectButton.swift` (`toConnected`) | Connect button: disconnected → connected. See MainConnectButton. |
| `TTD.json` | `Lotties/Connect/TTD.json` | `UI/MainConnectButton.swift` (`toDisconnected`) | Connect button: connected → disconnected. |
| `Lock.json` | `Lotties/Lock.json` | `UI/OnboardingScreen.swift` (slide 1) | Onboarding slide 1. See Onboarding. |
| `Globe-and-pins.json` | `Lotties/Globe-and-pins.json` | `UI/OnboardingScreen.swift` (slide 2) | Onboarding slide 2. |
| `Speedometer.json` | `Lotties/Speedometer.json` | `UI/OnboardingScreen.swift` (slide 3) | Onboarding slide 3. |
| `Shield.json` | `Lotties/Shield.json` | `UI/OnboardingScreen.swift` (slide 4) | Onboarding slide 4. |
| `Logo.json` | `Lotties/Logo.json` | `UI/SplashScreen.swift` | Splash logo. See SplashScreen. |

## In the repo, not used by code
`Lotties/Connect/TTF.json`, `DTF.json` and `FTD.json` are in the repo, but no Swift code loads them on `main@00e1b7b`. They are not copied here.

## Notes
- The previews play these files with the local copy of `lottie-web` 5.12.2 in `vendor/lottie-web-5.12.2/` (MIT licence file beside it). They need no network, but HTTP (a `file://` page cannot load the JSON).
- Arabic: the Connect button forces left-to-right on its animation (`MainConnectButton.swift:111`), so `TTC` and `TTD` never mirror. The onboarding and splash code sets no flip; whether the Lottie view mirrors there in Arabic is to confirm.
