# Flags

Country flags, copied with no change from `native/SecureFieldApp/SecureFieldApp/Resources/Assets.xcassets/flags/` (48 files). Each file is named by its ISO 3166 code in upper case. `EARTH.svg` is the Auto location.

## Where they are used
- iPhone server rows and main server view: `UI/ServerListScreen.swift:198`, `UI/MainScreen.swift:1499`. Size 35 × 35 in ServerItem.
- iPad server column: `UI/WideServerList.swift:165`.
- Mac: `FlagView` (`native/Design/Brand.swift:205`), clipped to a circle with a 1 pt white 25 % ring. Sizes: 30 (location rows), 24 (panel location row), 26 (tiles, not used on main), 18 (window detail under the status).

The code asks for `flags/<imageCode>` from the backend. When a code has no file, it shows `EARTH`. Which codes the backend sends is data, not design.

## Right-to-left
Flags never mirror.
