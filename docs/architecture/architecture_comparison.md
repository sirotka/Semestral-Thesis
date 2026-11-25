# Comparison of FPGA Platform Architectures

This section examines two options for a custom printed circuit board (PCB) for the BPC-DE1 educational projects. In the first option, the FPGA is mounted directly onto the board. In the second option, a ready-made FPGA module (SoM) is mounted on a specially designed carrier PCB.

## 1. Hardware Components

| Component | Option A. Discrete FPGA on its own PCB | Option B. FPGA SoM on its own carrier PCB |
|---|---|---|
| FPGA | The chip is mounted directly on the educational PCB | The FPGA is already mounted on the module |
| FPGA Power Supply | Design of power converters, power sequencing, and power distribution for the required voltage rails | Part of the power supply is implemented on the SoM. The carrier PCB handles the input power supply, peripheral power supply, and, for some modules, the VCCIO bank power supply |
| Configuration | On-chip or external configuration memory, depending on the FPGA | Configuration memory is typically installed on the module, but its presence depends on the specific model |
| Programming | The JTAG connector and necessary boot circuits are designed on the PCB | On-board USB-JTAG or JTAG via the SoM connector are possible. An external programmer may still be required |
| Clock | External reference clock source connected to the FPGA clock input | The clock generator is often located on the module. The availability of additional clock signals depends on the SoM design |
| Peripheral Connection | Direct assignment of FPGA I/O to LEDs, buttons, indicators, and connectors | Assignment is limited to signals brought out to the SoM connector |
| Two educational Pmods | 16 separate FPGA I/O when using two 8-signal Pmods | At least 16 available I/O with compatible logic levels |
| Removable video output | Video output via a separate connector on the board | Video output via SoM pins and a separate carrier connector |
| Mechanical Connection | No additional board-to-board connector required for the FPGA | Compatible mating connectors, mounting, and adherence to module dimensions are required |
| Manufacturing | Assembly of the FPGA itself, including a more complex process for BGA | The FPGA is assembled by the SoM manufacturer, but connector assembly and carrier fabrication remain |
| FPGA Replacement | Typically requires a new PCB revision | A compatible SoM can be replaced without modifying the carrier PCB, provided the mechanical dimensions, pinout, and electrical parameters match |

## 2. GPIO and Video Output Connection

For comparison, the same set of educational peripherals is considered, featuring a separate interface to the TFP410 external video transmitter.

| Interface | Number of FPGA I/O |
|---|---:|
| 4 LEDs | 4 |
| 4 buttons | 4 |
| 2-digit 7-segment display with ten control lines | 10 |
| 2 Pmods (8 signals each) | 16 |
| TFP410 video interface, 12-bit dual-edge data, pixel clock and synchronization signals | 16 |
| Total | 50 |

For Option A, the number of available signals is determined by the FPGA package, the assignment of dedicated pins, and the distribution across banks. For Option B, the SoM connector pins and signals already in use on the module are also taken into account. The number of physical connector pins is not equal to the number of available GPIOs.

The video module is connected separately from the two educational Pmods. The TFP410 transmitter is considered an option for converting parallel digital video signals to TMDS. An audio path is not provided.

## 3. Impact of FPGA Internal Blocks

| Internal Resource | Impact on Architecture |
|---|---|
| PLL and clock network | Generates operating frequencies for the logic and video path. The presence of a PLL does not eliminate the need for a reference clock signal |
| Internal oscillator | Can be used for certain functions if its parameters meet the project requirements |
| BRAM and distributed memory | Storage of states, symbol tables, and data for educational projects without external RAM |
| DSP and hardware multipliers | Execution of arithmetic operations without implementing the entire multiplier in LUTs |
| Hardware I²C and SPI | If present in a specific FPGA, they reduce programmable logic resource usage. If absent, controllers can be implemented in HDL |
| PWM and LED drivers | Specialized blocks are not available in all families. For educational projects, PWM can also be implemented in HDL |
| DDR I/O and serializers | Affect the possible architecture of the digital video output. DDR support does not imply automatic compatibility with HDMI |
| Configuration Flash | On-chip memory may eliminate the need for a separate configuration Flash chip in the FPGA circuit |

## 4. Comparison of Specific Candidates

| Candidate | Architecture | FPGA I/O and Logic Levels | Package or Module Connector | Features |
|---|---|---|---|---|
| Lattice LFE5U-25F-7TG144C | A | Up to 98 User I/O, voltage set by banks | TQFP144 | EBR, DSP, PLL, open HDL toolchain, external configuration Flash, no on-chip SERDES |
| Gowin GW1N-LV9LQ144C6/I5 | A | Number of User I/O depends on specifications for LQ144, supports LVCMOS33 | LQFP144 | PLL, internal oscillator, BSRAM, hardware multipliers, and on-chip configuration Flash |
| Numato Narvi S7 | B | The manufacturer specifies 130 I/Os. In the V2.0 schematic, banks 14, 15, 16, and 35 have a VCCO of 3.3 V, while bank 34 has a VCCO of 1.5 V | Multi-pin connectors | Spartan-7, USB-JTAG, configuration, and power on the module |
| Trenz TE0712-03-42I36-A | B | I/O distribution and bank availability are determined by the schematic for this build. Part of the VCCIO is supplied from the carrier | Three Samtec LSHM Board-to-Board Connectors | Artix-7, DDR3, and Si5338 programmable clock generator |
| Trenz TEG2000-01-A1I-1A | B | Up to 116 native I/O pins according to the module documentation. Main logic levels are below 3.3 V; some lines have level shifters | Two Board-to-Board Connectors | GateMate A1, 16 MB QSPI Flash, 8 level-shifted I/O at 3.3 V |

## 5. Advantages and Limitations

| Architecture | Advantages | Limitations |
|---|---|---|
| A. Discrete FPGA | Direct access to package pins. Freedom to place peripherals. No SoM connector. TQFP/LQFP mounting is possible instead of BGA | Requires development of the complete power supply, configuration, JTAG, and clocking for the FPGA. More circuit design work and testing required during initial startup |
| B. FPGA SoM and carrier PCB | The FPGA is already mounted and equipped with some support circuits. The carrier PCB can be focused on educational peripherals. Potentially easier to replace the module | Limitations of the connector and pinout. Separate VCCIO and level shifters may be required. Additional costs for the module, mating connectors, and mounting |

## 6. Cost Comparison

| Cost Item | Option A | Option B |
|---|---|---|
| FPGA | Separate chip | Included in the SoM price |
| Configuration Flash | Depends on the FPGA | Typically included in the SoM |
| FPGA Clock Generator and Power Supply | External components on the main PCB | Partially or fully on the SoM |
| FPGA Assembly | Included in PCB assembly | Performed by the SoM manufacturer |
| Board-to-Board Connectors | Not required for the FPGA | Matching connectors and fasteners required |
| Peripherals, Pmods, and video module | Additional cost | Additional cost |
| PCB design | Main PCB with FPGA and peripherals | Carrier PCB with module connectors and peripherals |

## 7. Technical Documentation

| Component | Documentation |
|---|---|
| Lattice ECP5 | [ECP5 product documentation](https://www.latticesemi.com/Products/FPGAandCPLD/ECP5) |
| Gowin GW1N-9 | [GW1N product documentation](https://www.gowinsemi.com/en/product/littlebee_fpga/), [UG114E pinout](https://cdn.gowinsemi.com.cn/UG114E.pdf) |
| Numato Narvi S7 | [User guide and schematic](https://numato.com/docs/narvi-spartan-7-fpga-module/) |
| Trenz TE0712 | [TE0712 technical resources](https://wiki.trenz-electronic.de/display/PD/TE0712+Resources) |
| Trenz TEG2000 | [TEG2000 technical resources](https://wiki.trenz-electronic.de/display/PD/TEG2000+Resources) |
| TI TFP410 | [TFP410 datasheet](https://www.ti.com/lit/ds/symlink/tfp410.pdf) |
| Pmod | [Pmod Interface Specification 1.2.0](https://digilent.com/reference/_media/reference/pmod/pmod-interface-specification-1_2_0.pdf) |
