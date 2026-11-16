# ProtocolRow

A row on the Protocols screen: the protocol name, the "Recommended" tag on Smart, a radio with a tick. Includes `RecommendedTag`.

Source: `UI/SettingsScreen.swift` (`ProtocolsScreen`, `ProtocolRow`, `RecommendedTag`). Protocol list: `VPNProtocol.selectable` in `SecureFieldDomain/Server.swift`.

## Protocols screen (layout width `lw`)
- One `GradientBorderCard`, width `lw × 0.915`, height `lw × 0.915 / 1.2` (297.4 at lw 390), 16 vertical padding. Rows share the height and are split by `RowSeparator`. Title bar: `LargeTitleBar` "Protocols" (`PROTOCOLS.HEADER.TITLE`).
- Rows in order: Smart (`PROTOCOLS.AUTO`), OpenVPN, Wireguard, Securefield Shield (`PROTOCOLS.AMNEZIAWG`), Hysteria2. Product names are not translated, except Smart ("الوضع الذكي").

## ProtocolRow
- Padding `lw × 0.055` horizontal (21.45). The whole row is the tap target.
- Leading: name in `Body1`, `--text-primary`; on Smart, gap 8, then `RecommendedTag`.
- Discouraged (blocked in the user's country): gap 16, a bold "!" in `Body1` at `--discouraged` (#E5484D); and a 1 pt `--discouraged` ring, radius 12, around the row. Its accessibility label is "Not recommended in your country".
- Trailing: a 30 × 30 slot.
  - `RadioButton`, variant green, diameter 30, with tick.
  - Applying (1.5 s after a tap): a system circular spinner, tint `--text-secondary`, in the same slot. Change animates ease-in-out 0.2 s. All rows ignore taps while it runs.

## RecommendedTag
- "RECOMMENDED" (`PROTOCOLS.RECOMMENDED`, uppercased; Arabic "موصى به"). Red Hat Display Bold 10 (13 on a tablet), tracking 0.6, `--text-secondary`, one line.
- Padding 8 / 4. Capsule fill `--background-tertiary` at 12 %, 1 pt `--border-quaternary` border.

## States
Not selected, selected (radio + tick), applying (spinner), discouraged (ring and "!"), discouraged + selected.

## Right-to-left
The name and tag are on the right, the radio on the left. The "!" stays after the name (to its left in Arabic).

## Preview notes
The spinner is a static stand-in for the system spinner.
