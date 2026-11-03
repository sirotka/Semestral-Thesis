
# DE1 Hardware Peripheral Requirements

Project: FPGA Development Platform for Digital Systems Education  
Course: BPC-DE1  
Revision: 2026-11-03  
Status: Preliminary

## 1. Peripheral Inventory

| Peripheral | Quantity | Usage in DE1 | Location | Status |
|---|---|---|---|---|
| Standard LEDs | 16 total (4 onboard + 12 external) | Lab 4; Project 1: PWM Breathing LED | Main PCB + Pmod | 4 onboard confirmed; external module not selected |
| Slide switches | 8 proposed | Lab 1: Logic Gates; Lab 2: Comparator; Project 1: PWM Breathing LED; Project 3: Digital Safe | Main PCB or Pmod | Not decided |
| Push buttons | 5 proposed | Lab 4: Counter; Lab 6: Debouncing; Projects 2–5 | Main PCB | Onboard confirmed; quantity not approved |
| Seven-segment display | 8 digits | Labs 3–5; Projects 2–6 | Main PCB or Pmod | Location and driver not selected |
| Buzzer | 1 proposed | Project 5: Alarm Clock | Main PCB with disconnect switch | Supervisor recommendation |
| HC-SR04 ultrasonic sensor | 1 | Project 6: Ultrasound HC-SR04 | Pmod | Location confirmed; interface not selected |
| UART interface | 1 TX; RX optional | Lab 7: UART Transmitter | Header or USB-UART bridge | Not selected |
| Clock oscillator | 1 (100 MHz proposed) | Labs 4–7; Projects 1–6 | Main PCB | Model and frequency not approved |
| Pmod connectors | Minimum 2 | Project 1: External LEDs; Project 6: HC-SR04 | Main PCB | Minimum confirmed |
| HDMI-compatible output | 1 | Platform requirement | Main PCB | Required; implementation not selected |
| FPGA programming interface | 1 | All laboratories and projects | Main PCB | Not finalized |
| Power input and voltage regulation | 1 input + required supply rails | All laboratories and projects | Main PCB | Partially selected |
| External LED expansion module | 12 LED channels | Project 1: PWM Breathing LED | Pmod | Not selected |
| HC-SR04 level adaptation | 1 interface | Project 6: Ultrasound HC-SR04 | External Pmod adapter | Not selected |

## 2. Laboratory Exercises

| Lab | Topic | Required Peripherals |
|---|---|---|
| Lab 1 | Logic Gates | Switches, LEDs |
| Lab 2 | Binary Comparator | Switches, LEDs |
| Lab 3 | Seven-Segment Decoder | Seven-segment display, switches |
| Lab 4 | Binary Counter | Clock, LEDs, seven-segment display, buttons |
| Lab 5 | Display Multiplexing | Multi-digit seven-segment display, clock |
| Lab 6 | Button Debouncing | Buttons, clock, LEDs or display |
| Lab 7 | UART Transmitter | UART TX, clock, PC receiver |

## 3. Verilog Group Projects 2026

| Project | Required Peripherals | Quantity |
|---|---|---|
| Project 1: PWM Breathing LED | LEDs, switch | 16 LEDs, 1 switch |
| Project 2: Digital Stopwatch (Lap) | Seven-segment display, buttons | 8 digits; button count unspecified |
| Project 3: Digital Safe | Switches, seven-segment display, buttons | Counts unspecified |
| Project 4: 7-Segment Snake | Seven-segment display, buttons | 8 digits; button count unspecified |
| Project 5: Alarm Clock | Seven-segment display, buttons, buzzer | 1 buzzer assumed; other counts unspecified |
| Project 6: Ultrasound HC-SR04 | HC-SR04, seven-segment display | 1 sensor assumed; display digit count unspecified |

## 4. Sources

- [DE1 Verilog Laboratory Repository](https://github.com/tomas-fryza/verilog-examples)
- [DE1 VHDL Laboratory Repository](https://github.com/tomas-fryza/vhdl-examples)
- Verilog Projects 2026 — group project assignments
- Supervisor feedback — 2026-10-29
