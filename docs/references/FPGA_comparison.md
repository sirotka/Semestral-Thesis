# Comparison of Individual FPGA Chips

When designing an educational board, it is not only the size of the programmable logic that matters, but also the hardware resources of the chip itself: clock generators and distribution, PLLs, on-chip memory, DSPs, specialized controllers, hardware support for LEDs, differential lines, configuration, and available user pins. The tables below do not confuse an FPGA hardware IP block with a software/HDL module that can be implemented in logic cells.

## 1. Logic, Memory, Arithmetic and I/O Resources

| Manufacturer / Part Number | Logic Resources | Flip-Flops (FF) | Internal RAM | DSP / Hardware Arithmetic | Max. User I/O per Package | Package |
|---|---:|---:|---| ---|---:|---|
| Lattice [LFE5U-25F-7TG144C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-7TG144C/18137321) | ≈24K LUT4 | ≈24K | 1,008 Kbit EBR | 28 × 18×18 | 98 | TQFP144 |
| Lattice [LFE5U-12F-6TG144C](https://www.latticesemi.com/Products/FPGAandCPLD/ECP5) | ≈12K LUT4 | check exact value | 576 Kbit EBR | 28 × 18×18 | 98 (check TG144 version) | TQFP144 |
| Lattice [LFE5U-25F-6BG256C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-6BG256C/9553918) | ≈24K LUT4 | ≈24K | 1,008 Kbit EBR | 28 × 18×18 | 197 (package value) | CABGA256 |
| Lattice [ICE40UP5K-SG48I](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40UP5K-SG48I/7785190) | 5,280 LUT4 | in family table | 120 Kbit EBR + 1,024 Kbit SPRAM | 8 × MAC16 | 39 | QFN48 |
| Lattice [ICE40HX8K-CT256](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40HX8K-CT256/3083585) | 7,680 logic cells | in HX documentation | 128 Kbit EBR | no integrated MAC16/DSP18 | 206 | CBGA256 |
| AMD [XC7A35T-1CPG236C](https://www.digikey.cz/en/products/detail/amd/XC7A35T-1CPG236C/5039071) | 33,280 logic cells / 5,200 slices | ≈41,600 | 1,800 Kbit BRAM | 90 DSP48E1 | 106 | CPG236 BGA |
| Gowin [GW1N-LV9LQ144C6/I5](https://cz.mouser.com/cs/ProductDetail/GOWIN-Semiconductor/GW1N-LV9LQ144C6-I5?qs=wnTfsH77Xs6N%2FyGezJZrJQ%3D%3D) | 8,640 LUT4 | 6,480 | 468 Kbit BSRAM + 608 Kbit User Flash (not RAM) | 20 × 18×18 | 121 | LQFP144 |
| Cologne Chip [CCGM1A1-BGA324](https://www.digikey.cz/cs/products/detail/cologne-chip/CCGM1A1-BGA324/16087879) | 20,480 CPE | 40,960 registers | 1,280 Kbit | shared resources, not equivalent to DSP48 | 162 | FBGA324 |
| Cologne Chip [CCGM1A2-BGA324](https://www.digikey.cz/en/products/detail/cologne-chip/CCGM1A2-BGA324/29722451) | 40,960 CPE | 81,920 registers | 2,560 Kbit | shared resources, not equivalent to DSP48 | 162 | FBGA324 |
| Intel/Altera [EP4CE6E22I7N](https://www.digikey.cz/cs/products/detail/altera/EP4CE6E22I7N/2295894) | 6,272 LE | do not equate to LE | 270 Kbit (M9K) | 15 × 18×18 | 91 | EQFP144 E22 |

## 2. Integrated Functional Blocks and Hardware Peripherals

| FPGA / Family | Clock Management | On-chip Oscillator | Hard I²C / SPI / UART | Hardware PWM / RGB LED | DSP / BRAM | Differential I/O and SERDES | Configuration / Special Features |
|---|---|---|---|---|---|---|---|
| ECP5-25 (both packages) | 2 PLLs, global clock network, DDR I/O primitives | Not to be considered a replacement for an external system clock without separate confirmation | No confirmed dedicated user I²C/SPI/UART controllers, soft HDL/IP available | LED PWM implemented in LUT/FF, no hard RGB driver specified | 28 multipliers, EBR | High-speed I/O with DDR, LFE5U without SERDES, unlike some LFE5UM/UM5G models | sysCONFIG, external SPI/QSPI Flash, JTAG |
| iCE40UP5K | 1 PLL | Integrated HF/LF oscillator resources | 2 hard I²C + 2 hard SPI, UART soft IP | Hard PWM and LED driver resources, pin assignments depend on the package | 8 MAC16, EBR + SPRAM | LVDS/pseudo-differential capabilities depend on the package, hard SERDES for HDMI is not specified | NVCM/external configuration available within the family, verify specific boot mode |
| iCE40HX8K | PLL and global clock network: as per the HX manual | For the exact package, no equivalent to the UP5K has been specified | I²C/SPI/UART are primarily soft logic, do not port the UP5K’s hard blocks | PWM / RGB via HDL | 128 Kbit EBR, no hard MAC16 | I/O DDR/differential limitations per package, no SERDES | External configuration, JTAG / SPI |
| AMD Artix-7 35T | Clock Management Tiles, MMCM/PLL and BUFG (resource counts in DS180) | Typically an external clock source for the board | UART/I²C/SPI available via HDL/IP, not dedicated MCU peripherals hard MCU peripherals | PWM/LED typically soft HDL | 90 DSP48E1, 1,800 Kbit BRAM | SelectIO/ISERDES/OSERDES. XC7A35T without GTP | XADC, external configuration Flash, JTAG. XADC is a true hard analog block |
| Gowin GW1N-9 | 2 PLLs, global clock network | on-chip oscillator (OSC) | Custom I²C/SPI/UART IP can be implemented in the fabric. I²C configuration mode is not the same as a hard I²C user controller | LED/PWM via HDL/IP, no dedicated hard RGB LED driver specified for GW1N-9 | 20 × 18 × 18, 26 BSRAM, 608 Kbit User Flash | DDR/LVDS/MIPI capabilities depend on the banks, hard MIPI RX for GW1N-9: 0 according to the manufacturer’s table | On-chip configuration Flash, JTAG, GowinCONFIG options |
| GateMate A1/A2 | 4/8 PLLs, respectively | External clock and dedicated clock resources (see DS1001) | UART/I²C/SPI via HDL/soft IP. on-chip hard controllers not confirmed | PWM/LED via HDL | 1,280/2,560 Kbit RAM, arithmetic from CPE | Dedicated SerDes pins for some variants. Do not consider this proof of HDMI support | SPI Flash/JTAG, I/O is generally up to 2.5 V |
| Intel Cyclone IV E EP4CE6 | 2 PLLs. global clocking | No confirmed on-chip oscillator as a substitute for an external clock source | Custom UART/I²C/SPI soft IP / FPGA fabric | PWM/LED via HDL | 15 multipliers, M9K RAM | LVDS via I/O pins. Cyclone IV E lacks an on-chip high-speed transceiver | JTAG, external configuration memory. no hard MCU |

## 3. Configuration and Programming

| Candidate | Configuration Memory | Programming and Debugging | Suitable HDL Workflow | Implications for Custom PCB |
|---|---|---|---|---|
| ECP5-25 | External SPI Flash, volatile SRAM | JTAG, openFPGALoader (compatible cable required) | Verilog/VHDL → Yosys/nextpnr-ecp5/Trellis | Clock, Flash, reset, JTAG, and power are designed separately |
| iCE40 UP5K | NVCM / SPI boot depending on configuration | iceprog / programmer | Yosys/nextpnr-ice40/IceStorm | QFN48 packaging, hard I²C/SPI save fabric, but few GPIOs |
| iCE40 HX8K | External SPI Flash | iceprog/JTAG via a compatible circuit | Yosys/nextpnr-ice40/IceStorm | BGA-256, high assembly complexity |
| Artix-7 | External QSPI configuration | JTAG | Vivado (XDC) | BGA power, configuration, XDC, and assembly |
| GW1N-9 | On-chip Flash (configuration) | JTAG / Gowin programmer | Gowin EDA, with a separate open-source flow for specific devices | LQFP144, fewer Flash components, but clock/VCCIO and boot sequence must be designed |
| GateMate A1/A2 | External Flash | JTAG, openFPGALoader with a compatible interface | Yosys/nextpnr target-version specific | BGA324, level shifters for Pmod |
| Cyclone IV E | External EPCS/EPCQ configuration | JTAG | Quartus | Design configuration and power supply according to the handbook |

## 4. Quantitative Assessment of Applicability to DE1

Example of simultaneously active FPGA I/O: 4 LEDs + 4 buttons + 10 lines for a two-digit multiplexed seven-segment display with DP + 16 for two educational Pmods + 16 for an external 12-bit DDR video transmitter = 50 individual FPGA signals. Extended research configuration = 61 with additional switches, UART, and control. This is only a preliminary logic budget. Physical allocation across I/O banks and DDR timing have not been determined.

| FPGA | Pin capacity relative to 50 GPIO | Technical limit for DE1 |
| ---|---|---|
| ECP5-25 TG144 | 98 > 50 | configuration/clock pins and VCCIO banks, separate Flash circuits |
| ECP5-25 BG256 | 197 > 50 | BGA assembly and verification of valid pin sites |
| iCE40UP5K SG48 | 39 < 50 | Local peripherals must be reduced, signals multiplexed, or external drivers used |
| iCE40HX8K CT256 | 206 > 50 | BGA assembly, bank mapping |
| Artix-7 XC7A35T CPG236 | 106 > 50 | BGA + vendor flow + clock/DDR routing |
| Gowin GW1N-9 LQ144 | 121 > 50 | special/config pins, LVCMOS33 banks, video timing |
| GateMate A1/A2 | 162 > 50 | I/O ≤2.5 V and general-purpose level shifting |
| Cyclone IV E E22 | 91 > 50 | precise package placement, power, and toolchain |

## 5. Manufacturing Complexity and Cost

| Item | Historical Price per Chip | Date and Seller | Total Cost Details |
|---|---:|---|---|
| LFE5U-25F-7TG144C | 482.44 CZK excluding VAT | 21.11.2026 to 22.11.2026, DigiKey CZ | external Flash, 3 rails, JTAG/USB, oscillator, assembly |
| LFE5U-12F-6TG144C | 337.47 CZK (tax base to be confirmed) | 21.11.2026 to 22.11.2026, market research | similar ECP5 circuit blocks |
| GW1N-LV9LQ144C6/I5 | 752.34 CZK (tax base to be confirmed) | 21.11.2026 to 22.11.2026, Mouser CZ | integrated configuration Flash, but not a complete BOM |
| EP4CE6E22I7N | 507.56 CZK (tax base to be confirmed) | 21.11.2026 to 22.11.2026, market research | external Flash, rails, PCB |
| GateMate A1/A2 | No comparable confirmed price available | Not specified | BGA, Pmod translators, assembly |

## 6. Comparative Advantages and Limitations

ECP5-25 TG144. Pros: ample GPIO, BRAM/DSP/PLL, widely used open-source flow, package suitable for testing. Cons: full FPGA power/config/clock/JTAG design, with risks associated with DDR video and bank assignment. The presence of LFE5U instead of LFE5UM should not be interpreted as the presence of SERDES.

GW1N-9 LQ144. Pros: 121 package GPIOs, PLL, oscillator, 20 hard multipliers, on-chip Flash, and an affordable QFP package. Cons: device-specific limitations on banks and boot, and the need to verify the exact HDL flow. The I²C/SPI cores in the manufacturer’s documentation require clarification as to whether they are indeed hard IP.

iCE40UP5K SG48. Pros: 2 hard I²C, 2 hard SPI, oscillator, LED/PWM, and 8 MAC16, which are useful for small educational and standalone projects. Cons: 39 available pins, fewer than the 50 I/O required in the proposed scenario. The peripheral layout would need to change or this package would need to be excluded.

Artix-7 35T. Pros: 90 DSP48E1s, advanced clock management, BRAM, XADC, Vivado, and tutorial examples. Cons: BGA, vendor-specific toolchain, verification of bank-dependent voltages and the video path.

GateMate A1/A2. Pros: plenty of GPIO, 4/8 PLLs, open-source tools, and documentation. Cons: BGA, voltage translation for 3.3 V Pmods, and an unverified HDMI path.

Cyclone IV E. Pros: 2 PLLs, multipliers, M9K BRAM, Quartus documentation. Cons: external configuration, less suitable for a fully open toolchain flow, package-specific limitations.
