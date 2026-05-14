# mtErgoSplit v2

A Lily58-style, 58-key split mechanical keyboard built around the nice!nano v2 microcontroller and the nice!view OLED display.

---

## Overview

| Feature    | Detail                                         |
| ---------- | ---------------------------------------------- |
| Layout     | Lily58-style, 5 rows × 14 columns              |
| Keys       | 58 including 2 x 4 key thumb row               |
| MCU        | nice!nano v2                                   |
| Firmware   | ZMK                                            |
| Connection | USB-C (wired) & Bluetooth Low Energy           |
| Display    | nice!view 160x68 OLED                          |
| Layers     | 4 (Base, Raise\_R, Raise\_L, Fn\_Keys)         |

---

## Hardware

### nice!nano v2

The nice!nano v2 is a Pro Micro replacement development board that has the same pinout as the Pro Micro, meaning it will work with almost any Pro Micro keyboard. The nice!nano also has a 3.7V lithium battery charger on board as well as a software level switch to cut off power to LEDs, which can eat 1mA each even when off!

**Details from the nicekeyboards website**

- Processor: nRF52840 chip
- Memory: 1 MB of Flash & 256 kB of RAM
- Connections: USB-C and Bluetooth Low Energy (BLE)
- Power: USB or 3.7 V LiPo (onboard charging circuit, MX1.25 connector)
- Clock: 32.768 kHz oscillator on board for real-time clock capabilities
- Battery voltage reader that reports battery percentage

### Display

The nice!view is an SSD1306 OLED replacement display with one additional pin to allow adding it to existing boards. It "boasts > 1,000 x power savings."

- Display: Sharp LS011B7DH03 display with 30 Hz refresh rate
- Resolution: 160 x 68 pixels; diagonal size 1.08"
- Dimensions: 36 x 14 x 2.9 mm 
- Power: 3.3 V
- Interface: 3-wire SPI

---

## Firmware

**ZMK:** Main (pre-release)

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

The board accepts a



