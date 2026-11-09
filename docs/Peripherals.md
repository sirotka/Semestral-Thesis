
# DE1 Hardware Peripheral Requirements

Project: FPGA Development Platform for Digital Systems Education (VUT FEKT) 
Revision: 09.11.2026
Status: Preliminary Layout

## 1. Onboard Inventory

| Peripheral | Quantity | Usage in DE1 | Location | GPIO | Status |
|---|---|---|---|---|---|
| Standard LEDs | 4 | Lab 4; Project 1: PWM Breathing LED | Main PCB | 4 | Not confirmed |
| RGB LED | 1 | Project 1: PWM Breathing LED | Main PCB | 3 | Not confirmed |
| Slide switches | 4 | Lab 1: Logic Gates; Lab 2: Comparator; Project 1: PWM Breathing LED; Project 3: Digital Safe | Main PCB | Not confirmed |
| Push buttons | 5 | Lab 4: Counter; Lab 6: Debouncing; Projects 2–5 | Main PCB | Not confirmed |
| 7-segment display | 2 digits | Labs 3–5; Projects 2–6 | Main PCB | 10 | Not confirmed |
| Buzzer | 1 | Project 5: Alarm Clock | Main PCB | 1 | Not confirmed |

## 2. Pmod Inventory

| Peripheral | Quantity | Usage in DE1 | Location | GPIO | Status |
|---|---|---|---|---|---|
| Standard LEDs | 12 | Project 1: PWM Breathing LED | Pmod | 12 | Not confirmed |
| 7-segment display | 6 digits | Labs 3–5; Projects 2, 4 | Pmod | TBD | Not confirmed |
| HC-SR04 ultrasonic sensor | 1 | Project 6: Ultrasound HC-SR04 | Pmod | 0 | Not confirmed |
| HDMI-compatible output | 1 | Platform requirement | 2x Pmod | 16 | Not confirmed |

| Power input and voltage regulation | 1 input + required supply rails | All laboratories and projects | Main PCB | Partially selected |
| External LED expansion module | 12 LED channels | Project 1: PWM Breathing LED | Pmod | Not selected |
| HC-SR04 level adaptation | 1 interface | Project 6: Ultrasound HC-SR04 | External Pmod adapter | Not selected |

## 3. Laboratory Exercises

| Lab | Topic | Peripherals |
|---|---|---|
| Lab 1 | Logic Gates | Switches, LEDs |
| Lab 2 | Binary Comparator | Switches, LEDs |
| Lab 3 | Seven-Segment Decoder | Seven-segment display, switches |
| Lab 4 | Binary Counter | Clock, LEDs, seven-segment display, buttons |
| Lab 5 | Display Multiplexing | Multi-digit seven-segment display, clock |
| Lab 6 | Button Debouncing | Buttons, clock, LEDs or display |
| Lab 7 | UART Transmitter | UART TX, clock, PC receiver |

## 4. Verilog Group Projects 2026

| Project | Peripherals | Required Module(s) |
| :--- | :---: | :---: | :---: | :--- | :--- |
| **1. PWM Breathing LED** | 16x LED, 1x Switch | Counter |
| **2. Digital Stopwatch (Lap)** | 8x 7-seg, Buttons | Counter, Debouncer |
| **3. Digital Safe** | Switches, 7-seg, Buttons | Debouncer |
| **4. 7-segment Snake** | 8x 7-seg, Buttons | Debouncer, Counter |
| **5. Alarm Clock** | 7-seg, Buttons, Buzzer | Debouncer |
| **6. Ultrasound HS-SR04** | HS-SR04 (Pmod), 7-seg | Counter, Debouncer |

## 5. Sources

- [DE1 Verilog Laboratory Repository](https://github.com/tomas-fryza/verilog-examples)
- [DE1 VHDL Laboratory Repository](https://github.com/tomas-fryza/vhdl-examples)
- Verilog Projects 2026 — group project assignments
- Supervisor feedback — 03.11.2026
