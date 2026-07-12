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

## Ironhorse View: standalone wireless companion

Ironhorse View is a separate, nice!nano-compatible Bluetooth macropad. It is
not an Ironhorse split peripheral: pair it with the host independently. Its
standard ZMK status screen reports the companion's own battery, Bluetooth
profile, and output state—not Ironhorse state.

### Connections

| Function | Pro Micro position | nRF52840 GPIO | Connect to |
|---|---:|---|---|
| OLED SDA | D2 | P0.17 | SSD1306 SDA |
| OLED SCL | D3 | P0.20 | SSD1306 SCL |
| Key 1: Bluetooth profile previous | D4 | P0.22 | One switch terminal |
| Key 2: Bluetooth profile next | D5 | P0.24 | One switch terminal |
| Key 3: output toggle | D6 | P1.00 | One switch terminal |
| Ground | GND | — | Other terminal of every switch and OLED GND |
| OLED power | VCC | 3.3 V | SSD1306 VCC |

```
                  nice!nano-compatible controller
  3.3V/VCC  ------------------------------------ OLED VCC
  GND       ------------+----------------------- OLED GND
                      +--[Key 1]--- D4 / P0.22
                      +--[Key 2]--- D5 / P0.24
                      +--[Key 3]--- D6 / P1.00
  D2 / P0.17 ---------------------------------- OLED SDA
  D3 / P0.20 ---------------------------------- OLED SCL
```

Each key is a direct, active-low input with the controller's internal pull-up:
wire one switch terminal to its listed pin and the other to the shared ground.
There is **no matrix and no diode**. All parts must share ground.

### OLED requirements and caveats

- Power the I2C display from **3.3 V only**. Do not connect a 5 V OLED supply
  or 5 V I2C pull-ups to the controller. The SDA/SCL pull-ups must terminate at
  3.3 V; many OLED modules already include them.
- This configuration expects an SSD1306 controller at I2C address `0x3C` and a
  128×64 panel. Verify the module's controller and address before wiring;
  look-alike modules can use another controller or `0x3D`.
- Nice!nano-compatible clone silkscreen and pinout can vary. Verify both the
  Pro Micro position and the nRF52840 GPIO against the specific controller
  before soldering.
- OLED panel colors are fixed physical properties of the panel (including
  single-color or blue/yellow variants); firmware cannot change them.
- The display can blank when the companion idles or sleeps. Pressing a key
  wakes the companion/display, so allow it to wake before expecting an update.
