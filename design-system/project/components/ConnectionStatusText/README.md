# ConnectionStatusText

The one-line status under the Connect button on iPhone and iPad.

Source: `UI/MainScreen.swift` (`ConnectionStatusText`), strings `MAIN.*`.

## Anatomy
- Text: `Subtitle1` (NAMU-1850 17 / 19.04), centred. Min frame 120 × 24.
- Colour: `--text-primary` (white); `--text-secondary` (lightGreen) only when connected.
- Dots: three 4 × 4 circles in the text colour, 1 pt apart plus 0.5 pt side padding, 2 pt after the text, bottom-aligned to the text baseline. Only while connecting or disconnecting.

## States and strings
| Label | Key | English | Arabic |
|---|---|---|---|
| idle | `MAIN.DISCONNECTED` | Tap to connect | اضغط للاتصال |
| connecting | `MAIN.CONNECTING` | Connecting | جارٍ الاتصال |
| optimizing | `MAIN.OPTIMIZING` | Analyzing network | جارٍ تحليل الشبكة |
| connected | `MAIN.CONNECTED` | Connected | متصل |
| disconnecting | `MAIN.DISCONNECTING` | Disconnecting | جارٍ قطع الاتصال |
| noConnection | `MAIN.NO_CONNECTION` | No internet connection | لا يوجد اتصال بالإنترنت |

"Optimizing" shows while connecting, once the app moves past the first protocol of its ladder.

## Motion
- Label change: fade out 0.3 s, swap, fade in 0.3 s (linear).
- Dots: each fades in over 0.25 s, 0.15 s apart; hold 0.3 s; all fade out 0.3 s; wait 0.55 s; repeat.

## Right-to-left
The dots follow the text (to its left in Arabic). The Arabic labels are longer; "لا يوجد اتصال بالإنترنت" must not be cut off.
