cmake_minimum_required(VERSION 3.13)

# This project keeps the original Arduino-style logic unchanged.
# For Pico SDK native builds, the source needs adaptation from Arduino APIs
# (pinMode/digitalWrite/delay + Keypad library) to pico-sdk equivalents.
project(pico_w_keypad_leds C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

add_executable(pico_w_keypad_leds
  src/main.cpp
)
