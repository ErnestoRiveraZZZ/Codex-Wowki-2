# Wiring and GPIO Mapping

## Components (from provided Wokwi design)
- 1x Raspberry Pi Pico / Pico W controller
- 1x 4x4 membrane keypad
- 12x LEDs
  - 8 blue LEDs (numeric group)
  - 4 red LEDs (A/B/C/D group)
- 12x 220Ω series resistors (LED current limit)
- 4x 1kΩ resistors (keypad row pull-up network to 3V3)
- Shared GND wiring for all LED cathodes

## Keypad GPIO Map
| Keypad Pin | Pico W GPIO | Firmware Array |
|---|---:|---|
| C1 | GP19 | `colPins[0]` |
| C2 | GP18 | `colPins[1]` |
| C3 | GP17 | `colPins[2]` |
| C4 | GP16 | `colPins[3]` |
| R1 | GP26 | `rowPins[0]` |
| R2 | GP22 | `rowPins[1]` |
| R3 | GP21 | `rowPins[2]` |
| R4 | GP20 | `rowPins[3]` |

## LED GPIO Map
| Logical LED | Label in Diagram | Pico W GPIO | Firmware Index |
|---|---|---:|---:|
| LED1 | `1` | GP11 | `ledPins[0]` |
| LED2 | `2` | GP10 | `ledPins[1]` |
| LED3 | `3` | GP9 | `ledPins[2]` |
| LED4 | `4` | GP8 | `ledPins[3]` |
| LED5 | `5` | GP7 | `ledPins[4]` |
| LED6 | `6` | GP6 | `ledPins[5]` |
| LED7 | `7` | GP5 | `ledPins[6]` |
| LED8 | `8` | GP4 | `ledPins[7]` |
| LED9 | `A` | GP3 | `ledPins[8]` |
| LED10 | `B` | GP2 | `ledPins[9]` |
| LED11 | `C` | GP28 | `ledPins[10]` |
| LED12 | `D` | GP27 | `ledPins[11]` |

## Power/Ground Notes
- LED cathodes connect to Pico GND.
- LED anodes route through 220Ω resistors to GPIO outputs.
- Keypad rows are additionally biased to 3V3 through 1kΩ pull-ups in the supplied diagram.

## Assumptions
- The supplied pin arrays in firmware are treated as the source of truth.
- Diagram references a Pico footprint; project target remains Pico W-compatible because GPIO behavior is the same for used pins.
