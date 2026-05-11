# mtErgoSplit v2

A Lily58-style, 58-key split mechanical keyboard built around the nice!nano v2 microcontroller and the nice!view OLED display..

---

## Overview

| Feature    | Detail                                         |
| ---------- | ---------------------------------------------- |
| Layout     | Lily58-style, 5 rows × 14 columns              |
| Keys       | 58 including 2 x 4 key thumb row               |
| MCU        | nice!nano v2                                   |
| Firmware   | ZMK                                            |
| Connection | USB-C (wired) & Bluetooth Low Energy           |
| Display    | nice!view 128x64 OLED                          |
| Layers     | 4 (Base, Raise\_R, Raise\_L, Fn\_Keys)         |

---

## Hardware

### MCU — Waveshare RP2040-LCD-0.96

A Raspberry Pi RP2040-based development board with a built-in 0.96" colour LCD. The display is initialised by the board firmware in portrait orientation (80×160 canvas) with correct colours — no custom display driver required.

- Processor: RP2040 dual-core ARM Cortex-M0+ @ 133 MHz
- Flash: 2 MB
- Display: ST7735S, 160×80 px (portrait: 80×160)
- USB: USB-C
- Power: USB or 3.7 V LiPo (onboard charging circuit, MX1.25 connector)

### Optional — Adafruit DS3231 Precision RTC Breakout

Without this module the keyboard's clock resets to 2000-01-01 00:00 on every power cycle. With it, date and time persist across power cycles via a CR2032 coin cell on the RTC board.

- Interface: I2C
- Accuracy: ±2 ppm (temperature-compensated)
- Backup: CR2032 coin cell (not included)
- Wiring: SDA → GP2, SCL → GP3, VCC → 3.3 V, GND → GND

To enable, replace the software RTC section in `code.py` with the DS3231 driver — see `wiring_and_build.md` for details.

---

## Firmware

**CircuitPython version:** 9.2.x
**KMK version:** latest from https://github.com/KMKfw/kmk\_firmware

### Required libraries (copy to `/CIRCUITPY/lib/`)

| Library                  | Source                            |
| ------------------------ | --------------------------------- |
| `kmk/`                   | KMK GitHub repo                   |
| `adafruit_display_text/` | Adafruit CircuitPython Bundle 9.x |
| `adafruit_bitmap_font/`  | Adafruit CircuitPython Bundle 9.x |

---

## Keymap

### Layer 0 — Base

	`    1    2    3    4    5  |  6    7    8    9    0    =
	TAB  Q    W    E    R    T  |  Y    U    I    O    P   BSPC
	CTL* A    S    D    F    G  |  H    J    K    L    ;    '
	SFT  Z    X    C    V    B  |  N    M    ,    .    /   SFT**
	     —   GUI  ALT  R_R  SPC | R_L  ALT  ENT  DEL   —

`*` CTL\_ESC: tap = Escape, hold = Left Control  
`**` SFT\_ENT: tap = Enter, hold = Right Shift

### Layer 1 — Raise\_R (hold R\_R)

Symbols on number row, arrow keys on right home row, brackets.

### Layer 2 — Raise\_L (hold R\_L)

F-keys (F1–F12) on left alpha rows, symbols on right.

### Layer 3 — Fn\_Keys (hold R\_R + R\_L)

Media keys: volume, mute, play/pause, previous/next. Keyboard reset on Q position.

---

## Display

The status display shows (top to bottom):

1. Keyboard name — pale yellow
2. Connection type (USB / BLE) — gray
3. Battery level — gray
4. *(blank)*
5. Active layer name — light blue, double height
6. *(blank)*
7. Current time — gray, double height
8. Current date — light gray

---

## Battery (optional)

The board has an onboard LiPo charging IC (ETA6096) and MX1.25 2-pin connector. A 3.7 V LiPo with integrated protection circuit connects directly. Charging occurs automatically via USB-C.

To enable battery level reporting, wire a 100 kΩ / 100 kΩ voltage divider between LiPo+ and GND, connect the midpoint to GP26, and set `_USE_BATTERY_ADC = True` in `code.py`.

---

## Known limitations

- **Clock resets on power cycle** without DS3231 RTC module
- **WPM tracking** not available in current KMK version
- **Wireless** not supported on this MCU without hardware modification
