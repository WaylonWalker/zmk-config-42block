# 42block Handwiring Guide

## IMPORTANT: This guide shows BOTTOM VIEW (UPSIDE DOWN)
All diagrams in this guide show the keyboard as viewed from the BOTTOM during assembly. When you flip the keyboard over, the layout will be reversed.

---

## Diagram 1: Complete Matrix Layout (Bottom View)

```
                    nRF52840 QFN48 (Bottom View)
                    +----------------------+
                    |         MCU          |
                    |                      |
                    |  P1.15  P1.13  P1.11 |
                    |   Col2   Col1   Col0 |
                    +----------------------+

COLUMNS (12 total, running down)
│
│   Col0   Col1   Col2   Col3   Col4   Col5   Col6   Col7   Col8   Col9   Col10  Col11
│   P1.11  P1.13  P1.15  P0.02  P0.29  P0.31  P0.17  P0.20  P0.22  P0.24  P1.00  P0.11
│   Pin46  Pin44  Pin42  Pin4   Pin31  Pin33  Pin19  Pin22  Pin24  Pin26  Pin34  Pin13
│
▼   ▼      ▼      ▼      ▼      ▼      ▼      ▼      ▼      ▼      ▼      ▼      ▼

■────■────■────■────■────■────■────■────■────■────■────■──── Row0 (P0.10, Pin12)
│ESC │ Q   │ W   │ E   │ R   │ T   │ Y   │ U   │ I   │ O   │ P   │BSPC│
■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■
│ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │
■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■
│ESC │ A   │ S   │ D   │ F   │ G   │ H   │ J   │ K   │ L   │ ;   │ '   │
■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■
│ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │
■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■─┴──■
│Shift│ Z   │ X   │ C   │ V   │ B   │ N   │ M   │ ,   │ .   │ /   │Ctrl│
■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■─┬──■
│ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │  │ │
│    │    │    │    │    │    │    │    │    │    │    │    │    │
│    ■────■────■────■────■────■────■────■────■────■────■────■──── Row2 (P1.04, Pin38)
│    │Ctrl │Alt  │GUI  │Enter│Space│Shift│
│    ■────■────■────■────■────■────■──── Row3 (P1.06, Pin40)
│
ROWS (4 total, running across)
```

---

## Diagram 2: Nice!Nano Clone Pinout (Bottom View)

### Nice!Nano-Compatible Pin Mapping Table

Clone silkscreen labels are not consistent. Use the Pro Micro position and
GPIO together, and verify the controller pinout before soldering.

| Pro Micro position | GPIO Pin | Function | Matrix Connection |
|--------------------|----------|----------|-------------------|
| D14                | P1.11    | Col0     | ESC / Shift |
| D15                | P1.13    | Col1     | Q / B |
| D18 / A0           | P1.15    | Col2     | W / V |
| D19 / A1           | P0.02    | Col3     | E / C |
| D20 / A2           | P0.29    | Col4     | R / V |
| D21 / A3           | P0.31    | Col5     | T / B |
| D2                 | P0.17    | Col6     | Y / N |
| D3                 | P0.20    | Col7     | U / M |
| D4 / A6            | P0.22    | Col8     | I / , |
| D5                 | P0.24    | Col9     | O / . |
| D6 / A7            | P1.00    | Col10    | P / / |
| D7                 | P0.11    | Col11    | BSPC / Ctrl |
| D16                | P0.10    | Row0     | Top row |
| D10 / A10          | P0.09    | Row1     | Second row |
| D8 / A8            | P1.04    | Row2     | Third row |
| D9 / A9            | P1.06    | Row3     | Bottom row |


**Power Pins:**
- RAW: Raw battery voltage input
- GND: Ground
- RST: Reset (P0.18)
- VCC: 3.3V regulated output

### Required Connections for 42block:

**COLUMN PINS** (connect to these Pro Micro positions):
- Col0: D14 (P1.11)
- Col1: D15 (P1.13)
- Col2: D18/A0 (P1.15)
- Col3: D19/A1 (P0.02)
- Col4: D20/A2 (P0.29)
- Col5: D21/A3 (P0.31)
- Col6: D2 (P0.17)
- Col7: D3 (P0.20)
- Col8: D4/A6 (P0.22)
- Col9: D5 (P0.24)
- Col10: D6/A7 (P1.00)
- Col11: D7 (P0.11)

**ROW PINS** (connect to these Pro Micro positions):
- Row0: D16 (P0.10)
- Row1: D10/A10 (P0.09)
- Row2: D8/A8 (P1.04)
- Row3: D9/A9 (P1.06)

---

## Diagram 3: Column and Row Connection Summary

### COLUMNS (12 total)
```
Col 0: P1.11 (Pin46) ──────────────────┐
Col 1: P1.13 (Pin44) ──────────────────┤
Col 2: P1.15 (Pin42) ──────────────────┤
Col 3: P0.02 (Pin4)  ──────────────────┤
Col 4: P0.29 (Pin31) ──────────────────┤
Col 5: P0.31 (Pin33) ──────────────────┤  Diode cathodes (banded end) point
Col 6: P0.17 (Pin19) ──────────────────┤  away from these column connections
Col 7: P0.20 (Pin22) ──────────────────┤
Col 8: P0.22 (Pin24) ──────────────────┤
Col 9: P0.24 (Pin26) ──────────────────┤
Col10: P1.00 (Pin34) ──────────────────┤
Col11: P0.11 (Pin13) ──────────────────┘
```

### ROWS (4 total)
```
Row0: P0.10 (Pin12) ───► ESC Q W E R T Y U I O P BSPC
Row1: P0.09  (Pin11) ───► ESC A S D F G H J K L ; '
Row2: P1.04  (Pin38) ───► Shift Z X C V B N M , . / Ctrl
Row3: P1.06  (Pin40) ───►           Ctrl Alt GUI Enter Space Shift
```

---

## Diagram 4: Matrix Position Map (Bottom View)

```
           Col0  Col1  Col2  Col3  Col4  Col5  Col6  Col7  Col8  Col9  Col10 Col11
           P1.11 P1.13 P1.15 P0.02 P0.29 P0.31 P0.17 P0.20 P0.22 P0.24 P1.00 P0.11
           Pin46 Pin44 Pin42 Pin4  Pin31 Pin33 Pin19 Pin22 Pin24 Pin26 Pin34 Pin13
Row0 P0.10 RC(0,0) RC(0,1) RC(0,2) RC(0,3) RC(0,4) RC(0,5) RC(0,6) RC(0,7) RC(0,8) RC(0,9) RC(0,10) RC(0,11)
Pin12   ESC   Q     W     E     R     T     Y     U     I     O     P     BSPC

Row1 P0.09  RC(1,0) RC(1,1) RC(1,2) RC(1,3) RC(1,4) RC(1,5) RC(1,6) RC(1,7) RC(1,8) RC(1,9) RC(1,10) RC(1,11)
Pin11   ESC   A     S     D     F     G     H     J     K     L     ;     '

Row2 P1.04  RC(2,0) RC(2,1) RC(2,2) RC(2,3) RC(2,4) RC(2,5) RC(2,6) RC(2,7) RC(2,8) RC(2,9) RC(2,10) RC(2,11)
Pin38   Shift Z     X     C     V     B     N     M     ,     .     /     Ctrl

Row3 P1.06                       RC(3,3) RC(3,4) RC(3,5) RC(3,6) RC(3,7) RC(3,8)
Pin40                             Ctrl   Alt    GUI    Enter  Space  Shift
```

---

## Wiring Instructions

### Step 1: Diode Installation
- Install one diode at each switch position
- Diode anode (non-banded end) connects toward the column connection
- Diode cathode (banded end) connects to the row wire

### Step 2: Column Wiring
- Solder all diode anodes in the same column together
- Run a wire from each column to the corresponding nRF52840 pin
- Use the pin mapping from Diagram 2 for exact connections

### Step 3: Row Wiring  
- Solder the other side of each switch in the same row together
- Run a wire from each row to the corresponding nRF52840 pin
- Rows use pull-down resistors as configured

### Step 4: Unused Matrix Positions
These positions should be left empty:
- RC(3,0), RC(3,1), RC(3,2) - Left side of bottom row
- RC(3,9), RC(3,10), RC(3,11) - Right side of bottom row

---

## Final Connection List

### Column Connections to nRF52840:
- Col0 (RC[*,0]): P1.11 → Pin46
- Col1 (RC[*,1]): P1.13 → Pin44  
- Col2 (RC[*,2]): P1.15 → Pin42
- Col3 (RC[*,3]): P0.02 → Pin4
- Col4 (RC[*,4]): P0.29 → Pin31
- Col5 (RC[*,5]): P0.31 → Pin33
- Col6 (RC[*,6]): P0.17 → Pin19
- Col7 (RC[*,7]): P0.20 → Pin22
- Col8 (RC[*,8]): P0.22 → Pin24
- Col9 (RC[*,9]): P0.24 → Pin26
- Col10 (RC[*,10]): P1.00 → Pin34
- Col11 (RC[*,11]): P0.11 → Pin13

### Row Connections to nRF52840:
- Row0 (RC[0,*]): P0.10 → Pin12
- Row1 (RC[1,*]): P0.09 → Pin11
- Row2 (RC[2,*]): P1.04 → Pin38  
- Row3 (RC[3,*]): P1.06 → Pin40

---

## REMINDER: BOTTOM VIEW
All diagrams show the keyboard from the bottom. When you flip the keyboard over for use, the layout will be mirrored left-to-right.

---

## Ironhorse View: wireless split peripheral

Ironhorse is the **central** and is the only part paired to a computer or
phone. View is a ZMK BLE split **peripheral**: it sends its nine switch
positions to Ironhorse and does not advertise or pair as an independent host
keyboard. Its SSD1306 is local to View; do not expect it to show Ironhorse's
active layer, host Bluetooth profile, or host connection state.

Flash `ironhorse-central` to Ironhorse and `ironhorse-view-peripheral` to
View. Do not interchange them.

Ironhorse reserves one BLE connection and bond for View, while retaining ten
host profiles (`BT_MAX_CONN` and `BT_MAX_PAIRED` are both 11).

### View wiring: top view, 3 × 3

Wire one terminal of **each** switch to the listed GPIO and the other terminal
to a shared GND rail. These are direct active-low inputs using internal
pull-ups: there is **no matrix and no diode**.

| Physical position | Switch function | Pro Micro position | nRF52840 GPIO |
|---|---|---:|---|
| top left | GAME / L1 | D4 | P0.22 |
| top middle | MIC | D5 | P0.24 |
| top right | RECORD | D6 | P1.00 |
| middle left | SCREENSHOT | D7 | P0.11 |
| middle | media previous | D8 | P1.04 |
| middle right | media next | D18 / A0 | P1.15 |
| bottom left | Android Home | D19 / A1 | P0.02 |
| bottom middle | Android Back | D20 / A2 | P0.29 |
| bottom right | Signal launcher | D21 / A3 | P0.31 |

```
                View, top/use-side view
       +-----------+-----------+-----------+
       | GAME / L1 |    MIC    |  RECORD   |
       | D4 P0.22  | D5 P0.24  | D6 P1.00  |
       +-----------+-----------+-----------+
       | SCREENSHOT| MEDIA PREV| MEDIA NEXT|
       | D7 P0.11  | D8 P1.04  | D18 P1.15 |
       +-----------+-----------+-----------+
       | ANDR HOME | ANDR BACK |  SIGNAL   |
       | D19 P0.02 | D20 P0.29 | D21 P0.31 |
       +-----------+-----------+-----------+
```

Nice!nano-compatible clone silkscreen can vary. Verify the Pro Micro location
and GPIO against the actual controller before soldering.

### View OLED wiring

| Function | Pro Micro position | nRF52840 GPIO | Connect to |
|---|---:|---|---|
| OLED SDA | D2 | P0.17 | SSD1306 SDA |
| OLED SCL | D3 | P0.20 | SSD1306 SCL |
| OLED power | VCC | 3.3 V | SSD1306 VCC |
| Ground | GND | — | SSD1306 GND and switch common rail |

Use an SSD1306 128×64 display at I2C address `0x3C`. Supply and I2C pull-ups
must be 3.3 V only; never connect 5 V supply or pull-ups to these pins.

### Key behavior

The first View key selects layer 3 from every layer except layer 3 itself; on
layer 3 it selects layer 1. Ironhorse keys retain their existing positions
0–41 and reversed physical transform. View occupies positions 42–50.

| View key | ZMK output | Intended Android/host action |
|---|---|---|
| GAME / L1 | `&to 3`; on layer 3, `&to 1` | gaming layer / layer 1 |
| MIC | F13 | Key Mapper mic trigger |
| RECORD | F14 | Key Mapper record trigger |
| SCREENSHOT | F15 | Key Mapper screenshot trigger |
| media previous | Consumer Previous Track | standard media previous |
| media next | Consumer Next Track | standard media next |
| Android Home | F16 | Key Mapper Home trigger |
| Android Back | F17 | Key Mapper Back trigger |
| Signal | F18 | Key Mapper Signal-launch trigger |

On a stock Pixel 6, configure Key Mapper bindings for F13–F18. Android and/or
Key Mapper may not distinguish every extended F-key on every keyboard or OS
version; if a trigger cannot be distinguished, substitute a keycode Key Mapper
does recognize. Key Mapper's Accessibility service must remain enabled and may
be interrupted by Android battery optimization or accessibility policy.
Android can restrict screen recording, microphone control, Home, Back, and app
launches; their final behavior depends on Key Mapper permissions, Android
version, lock state, and the target app. The firmware sends only the listed HID
events and cannot bypass those restrictions.

### First split boot and host pairing

1. If View was previously flashed as the standalone macropad, or either
   controller has an old split bond, first complete the reset procedure below.
   Otherwise flash the corresponding central and peripheral images above.
2. With neither half carrying an incompatible split bond, power Ironhorse and
   View at the same time. The unbonded View automatically bonds to the central;
   it is not shown as a host-pairable keyboard.
3. After the split is connected, put Ironhorse in its normal host-pairing mode
   using its existing keymap/profile controls, then pair **Ironhorse** from
   Android's Bluetooth settings. Do not look for or pair View.
4. Select the intended Ironhorse Bluetooth profile and test a View key. When
   Ironhorse is USB-powered, select Bluetooth output before testing Android
   BLE input if its existing configuration defaults to USB output.

### Recovery: validated settings reset

This repository builds two named copies of ZMK's supported `settings_reset`
shield: `ironhorse-central-reset` and `ironhorse-view-peripheral-reset`. They
are intentionally built **without** `ironhorse` or `ironhorse_view`; this is
the pinned ZMK procedure. Each runs once to clear the controller's persistent
settings partition, including split bonds, host Bluetooth bonds/profiles,
output selection, and other saved settings.

Use this procedure when migrating from the former standalone View firmware or
when the halves fail to pair after confirming the normal images are on the
correct controllers:

1. Put both controllers in bootloader mode.
2. Flash `ironhorse-central-reset` to Ironhorse and
   `ironhorse-view-peripheral-reset` to View.
3. Flash `ironhorse-central` to Ironhorse and
   `ironhorse-view-peripheral` to View immediately afterwards.
4. Power both halves together so they make a new split bond, then forget the
   old Ironhorse keyboard on every host and pair Ironhorse again.

The reset firmware has Bluetooth disabled, so neither half is pairable until
its normal firmware has been restored. Resetting either half alone is not a
split-pairing recovery; reset both halves, and expect all host bonds to be
lost.
