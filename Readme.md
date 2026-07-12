# 42block

This is my zmk config for my handwired 42 key monoblock travel board designed to rest on top of a laptop comfortably without pressing any keys 
underneath it.  It prints in two solid chunks that are glued together.  Its thick enough that keys will not protrude up so that it can be flipped over and stuffed in a bag facing the laptop.


![42block](https://github.com/user-attachments/assets/e42129ac-5e9f-4919-964a-d230ac8909a2)

## Build artifacts

- `42block` — 42-key monoblock keyboard.
- `portajohn` — existing Portajohn build.
- `ironhorse-central` — Ironhorse central build. It pairs with host devices
  and receives View's split input.
- `ironhorse-view-peripheral` — nine-key Ironhorse View BLE split peripheral
  with a local SSD1306 display. It is not a host-pairable keyboard.
- `ironhorse-central-reset` / `ironhorse-view-peripheral-reset` — validated
  settings-reset images for clearing both halves before re-pairing.

See [HANDWIRING_GUIDE.md](HANDWIRING_GUIDE.md) for View wiring, split pairing,
and Android Key Mapper limitations.
