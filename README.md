# Pico W Keypad-to-LED Controller

## Overview
This repository packages a Raspberry Pi Pico W project that reads a 4x4 membrane keypad and controls 12 LEDs. The source logic is preserved exactly as provided (Arduino-style `setup()`/`loop()`, `Keypad.h`, `digitalWrite`).

## Repository Structure
- `src/main.cpp` - original application logic (unchanged behavior)
- `include/` - reserved for headers
- `docs/wiring.md` - wiring details, component list, and GPIO map
- `docs/architecture.md` - software architecture and behavior mapping
- `diagram.json` - Wokwi hardware diagram artifact
- `CMakeLists.txt` - minimal project scaffold for C/C++ layout

## Features
- 4x4 keypad scan via row/column GPIOs
- 12 individual LED channels
- Key-to-action mapping:
  - `1..8`: turn on corresponding blue LED
  - `9`: turn on blue LED bank (1..8)
  - `0`: turn off blue LED bank (1..8)
  - `A..D`: turn on corresponding red LED
  - `*`: turn on red LED bank (A..D)
  - `#`: turn off red LED bank (A..D)

## Target Platform
- Board: **Raspberry Pi Pico W (RP2040 + CYW43439 Wi-Fi)**
- Note: Current firmware does not use Wi-Fi.

## Run in Wokwi
1. Create a new Raspberry Pi Pico project in Wokwi.
2. Paste `src/main.cpp` into the code editor.
3. Paste the provided full `diagram.json` (from your design) into Wokwi's `diagram.json`.
4. Ensure Arduino-compatible Pico environment and `Keypad` library availability.
5. Start simulation and press keypad keys.

## Run on Real Hardware
1. Build with your preferred Arduino-compatible RP2040 toolchain (e.g., Arduino IDE with Pico core).
2. Flash the generated UF2 to Pico W in BOOTSEL mode.
3. Wire hardware as documented in `docs/wiring.md`.
4. Power cycle and verify keypad/LED responses.

## Pico SDK Note
This repo includes a C/C++ folder layout and CMake scaffold for organization. Native pico-sdk compilation would require API migration from Arduino calls (`pinMode`, `digitalWrite`, `delay`) and keypad library integration, which is intentionally not done to preserve core logic.

## Wi-Fi Credentials Guidance
No Wi-Fi credentials are used in this project. If Wi-Fi is added later:
- Keep credentials in a local, ignored config file.
- Do not hardcode secrets in source.
- Use environment- or build-time injection.
