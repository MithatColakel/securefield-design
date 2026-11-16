# Images

Images, copied with no change from `native/SecureFieldApp/SecureFieldApp/Resources/Assets.xcassets/`.

| File | Size | Used in |
|---|---|---|
| `World-Map.png` | 1500 × 2576 | Map over the page gradient, blend mode overlay. iPhone/iPad `GradientBackground` (`UI/GradientBackground.swift:47`); Mac `BrandBackground` (`native/Design/Brand.swift:116`, welcome and permission). Not used in the Mac main window or panel. |
| `Advertisement-Background.png` | 1500 × 1187 | Advertisement screen top (`UI/AdvertisementScreen.swift:164`). |
| `Heart-Rate.svg` | vector | FeedbackSheet art (`UI/FeedbackSheet.swift:92`). Full colour in the file. |
| `Connect.svg` | vector | In the catalog, but no Swift code on `main@00e1b7b` loads it (the iPhone Connect button is a Lottie; the Mac one is drawn in code). Kept as a file so the set matches the repo. |
