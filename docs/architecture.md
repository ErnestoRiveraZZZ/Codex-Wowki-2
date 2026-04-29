# Software Architecture

## High-Level Flow
1. Initialize 12 LED GPIOs as outputs and drive all LOW in `setup()`.
2. Poll keypad continuously in `loop()` using `keypad.getKey()`.
3. If a key event exists, execute a `switch` branch to drive one LED or a LED bank.
4. Sleep 10ms between loop iterations.

## Module Breakdown
- **Input module**: `Keypad` instance with static keymap + row/column pin arrays.
- **Output module**: `ledPins[]` output bank of 12 channels.
- **Control logic**: `switch(key)` mapping keypad events to output writes.

## Key Behavioral Map
- Single-key direct ON: `1..8`, `A..D`
- Group ON: `9` (numeric LEDs), `*` (alpha LEDs)
- Group OFF: `0` (numeric LEDs), `#` (alpha LEDs)

## Non-Functional Characteristics
- Polling-based control loop.
- No dynamic allocation.
- No RTOS dependency.
- No networking usage even on Pico W hardware.

## Portability Note
Current source is Arduino-style C++. For strict pico-sdk portability, the same logic can be preserved while replacing hardware API calls with pico-sdk equivalents. This repository intentionally keeps original behavior and control structure untouched.
