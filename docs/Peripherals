# DE1 Hardware Peripheral Requirements and Placement

**Project:** FPGA Development Platform for Digital Systems Education  
**Course coverage:** BPC-DE1 laboratory exercises and 2026 Verilog group projects **only**  
**Prepared for:** doc. Ing. Tomáš Frýza, Ph.D.  
**Revision:** 2026-11-03  preliminary review, **not an approved BOM**

## 1. Peripheral inventory

The **Quantity** column is the proposed platform capacity (or a documented project minimum), **not** a claim that every task requires all devices simultaneously. *Onboard* means mounted on the main PCB; *Pmod* means connected using a removable module. Where exact assignment quantities have not been verified, these are expressly marked as proposals.

| Peripheral / hardware resource | Quantity for the platform | Where it is used | Proposed location | Decision status |
|---|---|---|---|---|
| Standard single-colour LEDs | **16 controllable LEDs total**: approximately **4 onboard + 12 external** | **Lab 4** binary counter/LED indication (implementation-dependent); **Project 1** PWM Breathing LED (explicitly 16 LEDs) | ~4 main PCB; 12 on Pmod LED expansion | **Supervisor direction confirmed** for ~4 onboard and the remainder through Pmod; external LED module **not selected** |
| Slide switches | **8 proposed**; assignment-confirmed minimum **1** for Project 1 | **Lab 1**  logic gates; **Lab 2** comparator (manual input signals, mapping to be checked); **Project 1** PWM Breathing LED (1 switch); **Project 3**  Digital Safe (unspecified count) | Main PCB **or** removable Pmod switch module | **Not decided**: count and location require supervisor approval |
| Momentary push buttons | **5 proposed**; exact course minimum not specified | **Lab 4**  counter control/reset where implemented; **Lab 6** debouncing; **Project 2** Digital Stopwatch; **Project 3** Digital Safe; **Project 4**  7-segment Snake; **Project 5**  Alarm Clock | Main PCB | **Onboard confirmed**; count **not approved** |
| Seven-segment display (digit positions) | **8 digits proposed and needed for Projects 2 and 4**; decimal-point connection to be confirmed | **Lab 3**  segment decoder; **Lab 4**  counter/display variant, if used; **Lab 5**  multiplexed multi-digit driver; **Projects 2–6**  Stopwatch, Safe, Snake, Alarm Clock, Ultrasound | Main PCB **or** removable display module | **Not decided**: whether onboard, which display type, driver, or connector; direct multiplexing is a proposal |
| Audible buzzer / piezo sounder | **1 proposed** | **Project 5**  Alarm Clock | Main PCB, with a physical disable switch **suggested** | **Supervisor suggestion**, not yet approved; active/passive type, driver and switch design **not selected** |
| HC-SR04 ultrasonic sensor | **1** | **Project 6**  Ultrasound HC-SR04 | External module through Pmod | **Pmod placement confirmed**; exact sensor variant, 5 V supply and Echo-level adaptation **not selected** |
| UART communication connection | **1 TX channel** required for **Lab 7**; RX provision **proposed** | **Lab 7**  UART transmitter | UART pins on header or via a USB–UART bridge (implementation TBD) | Function required; physical bridge/connector and RX provision **not selected** |
| Clock oscillator | **1 proposed** (100 MHz tentative) | **Lab 4**  counter; **Lab 5**  multiplexing; **Lab 6**  debounce; **Lab 7**  UART; **Projects 1–6**  synchronous timing/PWM/control | Main PCB | Onboard clock required by system concept; oscillator part/frequency **not yet approved** |
| Pmod expansion connectors | **2 minimum**, third optional | **Project 1**  additional LED outputs; **Project 6**  HC-SR04; other removable interfaces | Main PCB | **Minimum 2 confirmed**; exact count/placement **not fixed** |
| HDMI-compatible digital video output | **1** | **Independent platform requirement**, not expressly required by Projects 1–6 or Labs 1–7 | Main PCB | **Confirmed requirement**; minimum video mode, TMDS interface method and circuit **not selected** |
| FPGA programming/configuration access | **1 programming/configuration path** | Required to load all DE1 laboratory and project designs onto hardware | Main PCB (Flash, programming/JTAG connector or bridge) | Requirement of a usable FPGA board; exact programming interface hardware **not final** |
| Board power input / voltage regulation | **1 board power input** plus FPGA-required power rails | All labs and projects; extra module power where applicable | Main PCB; external power for 5 V/actuator modules when needed | System-level need; selected 3.3 V buck **TPS62142RGTT**, remaining power-tree details pending |
| External LED expansion hardware | **Capacity for 12 additional independently controllable LEDs** with the ~4 onboard plan | **Project 1**  PWM Breathing LED | Removable Pmod LED module(s) | **Needed to cover assignment**, but module count/driver topology **not selected** |
| HC-SR04 power and level interface | **1 adapter/interface as needed** | **Project 6**  Ultrasound HC-SR04 | External Pmod adapter or electrically safe module | **Not selected**; verify sensor variant; typical 5 V Echo must not be applied directly to 3.3 V FPGA I/O |

## 2. How the resources map to DE1 assignments

### Laboratory exercises (Lab 1–7)

| Laboratory | Course topic | Main physical resources to consider | Verification note |
|---|---|---|---|
| **Lab 1** | Logic gates | Switch inputs; LED outputs | Exact counts and any on-board execution requirement need verification from full Lab 1 instructions |
| **Lab 2** | Binary comparator | Switch inputs; LED outputs if implemented physically | Exact mapping/count not established from repository overview |
| **Lab 3** | Seven-segment display decoder | Seven-segment digit, optional switch inputs | Specific board-level pin allocation to verify |
| **Lab 4** | Binary counter | Clock, LED indicators and/or seven-segment display, possible button reset | Exact wiring and variants must be checked against full lab README |
| **Lab 5** | Multiple seven-segment displays | Multiplexed 7-segment display, clock | The platform should preserve the ability to teach multiplexed display driving; physical architecture pending |
| **Lab 6** | Button debounce | Push button, clock; LED or display for visible feedback if used | Exact feedback peripheral depends on the lab variant |
| **Lab 7** | UART transmitter | UART TX and suitable receiver/monitor on a host computer; clock | An RX pin or USB bridge is an optional convenience, not proven mandatory for Lab 7 |

### Verilog group projects 2026

| Project | Hardware specified in the provided assignment | Quantity explicitly given or inferred from singular wording |
|---|---|---|
| **Project 1  PWM Breathing LED** | LEDs; switch | **16 LEDs; 1 switch** |
| **Project 2  Digital Stopwatch (Lap)** | 7-segment display; buttons | **8 digits; buttons (count unspecified)** |
| **Project 3  Digital Safe** | Switches; 7-segment display; buttons | **Counts unspecified** |
| **Project 4  7-segment Snake** | 7-segment display; buttons | **8 digits; buttons (count unspecified)** |
| **Project 5  Alarm Clock** | 7-segment display; buttons; buzzer | **Display/button counts unspecified; one buzzer assumed** |
| **Project 6  Ultrasound HC-SR04** | HC-SR04 via Pmod; 7-segment display | **One sensor assumed; display digits unspecified** |

## 3. Supervisor confirmations vs. choices still pending

### Confirmed supervisor instructions

- Approximately **4 simple LEDs on the main PCB**, with additional LEDs connected through **Pmod**.
- **Push buttons on the main PCB**; no numerical count specified in the supervisor's reply.
- **HC-SR04 via Pmod**, rather than placing the sensor on the main PCB.
- At least **2 Pmod connectors**, with the possibility of more.
- **HDMI-compatible video output** is mandatory; **VGA is not required**.
- The platform shall support **DE1 laboratory exercises and group projects**; **DE2 is outside the scope of this requirements document**.

### Suggested by supervisor, but not mandatory yet

- **One onboard buzzer with a small physical switch to disconnect it.**

### Not yet selected or approved

- Whether **8 slide switches** are needed and whether they are **onboard or external**.
- Whether the **8-digit seven-segment display** is **onboard or external**, and what driver topology is acceptable for the display-multiplexing laboratory.
- Whether **5 onboard push buttons** are sufficient.
- Whether to use **2 or 3 Pmod connectors** and which external LED expansion design covers all 16 LED channels.
- Buzzer type, physical disconnect scheme and driver.
- UART-to-PC connection hardware, oscillator part, exact Pmod adapter electronics, and HDMI video implementation / minimum video mode.
- Pin-bank feasibility, IO voltage domains, simultaneous use of connectors and exact FPGA pin assignments.

## 4. Short questions for the supervisor

1. **Should the eight-digit seven-segment display be onboard or connected as an external module?** For Lab 5, must students control its multiplexing directly from FPGA pins?
2. **Should slide switches be onboard or external via Pmod, and are eight switches sufficient?**
3. **Are five onboard push buttons sufficient for all DE1 projects?**
4. **What minimum HDMI-compatible video resolution and refresh rate should the board support?**

The minimum two Pmod connectors, onboard ~4 LEDs, extra LEDs via Pmod, HC-SR04 via Pmod, and the semester's **design-only** deliverable are already known; they need not be asked again.

## 5. Outside the verified DE1 scope

RGB LEDs, NeoPixel, OLED, BME280, dedicated SPI/I2C sensor modules, ADC/microphone, servo/motor interfaces and Wi-Fi modules **must not automatically be added as mandatory components** based on unrelated Pico W/MicroPython group-project material. They may be considered optional expansions only after a specific DE1 need has been demonstrated.

## Sources and evidence

- Official **[DE1 Verilog laboratory repository](https://github.com/tomas-fryza/verilog-examples)**  topics and lab numbering, reviewed 2026-11-03.
- Official **[DE1 VHDL laboratory repository](https://github.com/tomas-fryza/vhdl-examples)**  equivalent lab structure, reviewed 2026-11-03.
- User-provided **“Verilog projects 2026”** assignment text  six group projects and explicit 16-LED / 8-digit assignments.
- Supervisor's written response, **2026-10-29 18:16**, confirming approximately four onboard LEDs, Pmod extensions and external HC-SR04; suggesting a disconnectable onboard buzzer.
- FPGA project requirements and architecture checkpoint v0.7 dated 2026-10-29  current proposed implementation details, **not** component approval.

**Status note:** No parts were added to or approved in the BOM by this document. All proposals must be reviewed for electrical safety and pin-budget feasibility before schematic capture.
