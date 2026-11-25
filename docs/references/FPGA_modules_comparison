# Comparison of FPGA Modules

This section examines modules with an FPGA installed that can be used on a dedicated carrier PCB. Full-featured debug boards are listed separately as design alternatives. The tables compare the FPGA's internal resources, the module's components, and the signals that are actually accessible through its connectors.

## 1. FPGA, Memory, and Module Connectors

| Manufacturer and Module | FPGA | Exposed FPGA I/O | Module Connector | External Memory and Clock | Programming |
| ---|---|---|---|---|---|
| Numato [Narvi S7](https://numato.com/product/narvi-spartan-7-fpga-module/) | Spartan-7 XC7S50, CSG324 | 130 I/O per manufacturer’s specifications | Multi-pin connectors | Configuration Flash, clock source, power supply circuits | FT2232H, JTAG, Vivado |
| Trenz [TE0712-03-42I36-A](https://wiki.trenz-electronic.de/display/PD/TE0712+Resources) | Artix-7 XC7A35T-2FGG484I | Up to 128 HR I/O according to this build’s table, including pins with alternative functions | 3 Samtec LSHM board-to-board connectors | 1 GB DDR3, 32 MB Flash, Si5338 clock generator | JTAG via connectors, Vivado |
| Trenz [TEG2000-01-A1I-1A](https://www.trenz-electronic.de/en/FPGA-module-with-GateMate-A1-from-Cologne-Chip-16-MByte-QSPI-Flash-4-x-5-cm/TEG2000-01-A1I-1A) | GateMate CCGM1A1 | Up to 116 native I/O according to design documentation, individual lines with level shifting | 2 board-to-board connectors | 16 MB QSPI Flash, clock source, power supply | JTAG, Yosys, and nextpnr |
| Machdyne [Sechzig ML1](https://machdyne.com/product/sechzig-ml1-compute-module/) | Lattice ECP5-45F | The exact number of available GPIOs on the connector is not specified | 60-pin edge connector | Memory and clock configuration depends on the version | JTAG, Yosys, and nextpnr |
| Machdyne [Sechzig ML2](https://machdyne.com/product/sechzig-ml2-compute-module/) | Lattice ECP5-45F | The number of available GPIOs depends on the pin assignments of the connector | 60-pin edge connector | Memory and configuration as shown in the schematic for the corresponding version | JTAG, Yosys, and nextpnr |
| MuseLab [iCESugar-Pro](https://www.tindie.com/products/johnnywu/icesugar-pro-fpga-development-board/) | Lattice ECP5-25F, BG256 | 106 GPIOs as described in the project | SO-DIMM 200 | 32 MB SDRAM, 32 MB SPI Flash, 25 MHz | iCELink via USB-C, Yosys, and nextpnr |
| apfaudio [SoldierCrab R3](https://github.com/apfaudio/soldiercrab) | Lattice ECP5-25F, BG256 | 47 GPIOs according to the project documentation | M.2 E-key | 32 MiB RAM, 16 MB SPI Flash, 48 MHz | JTAG, open-source HDL toolchain |
| Sipeed [Tang Primer 20K Core](https://wiki.sipeed.com/hardware/en/tang/tang-primer-20k/primer-20k.html) | Gowin GW2A-LV18 | Published descriptions list 103 and 117 signals, depending on the counting method | SO-DIMM 204 | DDR3, Flash, clock source | Gowin EDA, boot via Dock or programmer |
| Digilent [Cmod A7-35T](https://digilent.com/shop/cmod-a7-35t-breadboardable-artix-7-fpga-module/) | Artix-7 XC7A35T | 44 DIP digital signals and 8 Pmod signals according to the documentation | DIP and Pmod | QSPI Flash, clock generator | USB-JTAG, Vivado |
| Digilent [Cmod S7](https://digilent.com/shop/cmod-s7-breadboardable-spartan-7-fpga-module/) | Spartan-7 | 32 digital I/O pins on DIP, with additional Pmod signals available | DIP and Pmod | Flash, clock generator | USB-JTAG, Vivado |
| Numato [Neso A7](https://numato.com/product/neso-artix-7-fpga-development-board) | Artix-7 XC7A100T | 140 I/O according to the published specifications | Multi-pin headers | RAM, Flash, clock source | USB, JTAG, Vivado |
| Numato [Skoll K7](https://numato.com/product/skoll-xilinx-kintex-7-usb-ready-to-go-fpga-module) | Kintex-7 XC7K70T | 150 I/O according to published specifications | Multi-pin connectors | Flash, clock source | USB, JTAG, Vivado |
| Trenz [TE0873](https://wiki.trenz-electronic.de/display/PD/TE0873+Resources) | Spartan UltraScale+, depends on part number | Exact value for selected part number not specified | Board-to-board | Memory and configuration depend on build | Vivado |
| Enclustra [Mars AX3](https://www.enclustra.com/en/products/fpga-modules/) | Artix-7, depends on part number | Up to 108 I/Os per previously discussed specification | SO-DIMM 200 | RAM, Flash, and clock source vary by variant | Vivado |
| Enclustra [Mercury+ KX2](https://www.enclustra.com/en/products/fpga-modules/) | Kintex-7, depends on part number | Up to 216 I/O per previously discussed specification | Board-to-board | DDR, Flash, and clock source vary by variant | Vivado |
| Critical Link [MitySOM Cyclone 10](https://www.criticallink.com/) | Intel Cyclone 10 LP or GX, depending on the variant | Up to 180 or 192 I/O in published variants | SO-DIMM or board-to-board, depending on the variant | DDR, configurable memory, clock sources | Quartus |

## 2. FPGA Internal Resources and Module Hardware

| Module | FPGA Clock | FPGA Hardware Blocks | On-Board Interface Controllers | Individual Module Components |
| ---|---|---|---|---|
| Narvi S7 | PLL, MMCM, Spartan-7 global clock network | DSP48E1, BRAM, XADC | I²C, SPI, and UART implemented via HDL or IP | FT2232H, Flash, system clock generator |
| TE0712 | PLL, MMCM, BUFG in Artix-7 | 90 DSP48E1, 1,800 Kbit BRAM, XADC | I²C, SPI, and UART via HDL or IP | 1 GB DDR3, 32 MB Flash, Si5338, auxiliary CPLD |
| TEG2000 | 4 PLLs in GateMate A1 | 20,480 CPEs, 1,280 Kbit of on-chip RAM | I²C, SPI, and UART via HDL or soft IP | 16 MB QSPI Flash, level shifters, regulators |
| Sechzig ML1 and ML2 | PLLs and global clock networks on the ECP5-45F | EBR and hardware multipliers from the ECP5 family | I²C, SPI, and UART via HDL or IP | Flash, memory, and oscillator depending on the board version |
| iCESugar-Pro | 2 PLLs in ECP5-25F | 28 18×18 multipliers, 1,008 Kbit EBR | I²C, SPI, and UART via HDL or IP | 32 MB SDRAM, 32 MB SPI Flash, iCELink, RGB LED |
| SoldierCrab R3 | 2 PLLs in ECP5-25F | 28 18×18 multipliers, 1,008 Kbit EBR | I²C, SPI, and UART via HDL or IP | RAM, SPI Flash, clock source |
| Tang Primer 20K Core | PLL and clock networks on the Gowin GW2A | BSRAM and hardware DSP resources on the GW2A | Support for interfaces via IP depends on the specific FPGA | DDR3, Flash, clock source |
| Cmod A7 | PLL, MMCM, and BUFG in Artix-7 | 90 DSP48E1, 1,800 Kbit BRAM, XADC | I²C, SPI, and UART via HDL or IP | USB-JTAG/UART bridge, Flash, and clock source |
| Cmod S7 | PLL, MMCM, Spartan-7 global clock network | DSP48E1, BRAM, XADC | I²C, SPI, and UART via HDL or IP | USB-JTAG, Flash, clock source |
| Neso A7 and Skoll K7 | PLL and MMCM specific to the FPGA | DSP48E1, BRAM, XADC, capacity depends on the device | Serial controllers are typically implemented via HDL or IP | USB interface, Flash, RAM depending on the configuration |
| TE0873, Mars AX3, Mercury+ KX2, MitySOM | Resources depend on the specific FPGA part number | DSP blocks, RAM, and other specialized resources depend on the device | The availability of hard IP is determined by the installed chip | Memory, configuration, and auxiliary ICs depend on the part number |

## 3. I/O, Power, and Peripheral Connections

| Module | I/O Voltage and Connector Limits | Use with Pmod and Video Module |
|---|---|---|
| Narvi S7 V2.0 | Banks 14, 15, 16, and 35 have a VCCO of 3.3 V. Bank 34 has a VCCO of 1.5 V in the circuit under investigation | Signals from compatible banks are suitable for 3.3 V Pmods. Level matching is required when using Bank 34 |
| TE0712-03-42I36-A | The VCCIO power supply for individual banks is provided by the carrier PCB. Connectors JM1, JM2, and JM3 carry signals from different banks | Custom routing of Pmod and video signals is possible, taking into account bank voltage, occupied pins, and GTP functions |
| TEG2000-01-A1I-1A | The banks' native I/O is limited to voltages below 3.3 V. Some signals pass through level shifters to 3.3 V | For two 3.3 V Pmods, a sufficient number of bidirectional level shifters will be required. The built-in shifted lines are not sufficient for all educational interfaces |
| Sechzig ML1 and ML2 | Of the 60 pins on the edge connector, some are used for power and service signals | The number of available GPIOs is fewer than the number of physical pins on the connector |
| iCESugar-Pro | SO-DIMM 200. Compatible levels are determined by the VCCIO bank and the module's pinout | The 106 declared GPIOs provide a margin over the base 50 signals, but the SO-DIMM connector complicates the carrier design |
| SoldierCrab R3 | M.2 E-key. 47 GPIOs announced | Three lines are missing for the base variant with 50 independent signals. The peripheral schematic will need to be modified or expanders will need to be used |
| Tang Primer 20K Core | SO-DIMM 204. Pin availability depends on the selected Core and Dock configuration | For Pmods and the 16-line video interface, reserved memory and configuration signals must be accounted for |
| Cmod A7 | Separate DIP and Pmod. The number of available signals is limited by the pinout | The ability to connect two Pmods and a video module simultaneously depends on the actual pin assignment |
| Cmod S7 | 32 digital I/Os on the DIP and separate Pmod resources | The basic set of interfaces is limited by the number of available GPIOs |
| Neso A7 and Skoll K7 | Multi-pin connectors, I/O power is determined by bank assignment | Integration with the carrier depends on the pinout table of the corresponding module |
| TE0873, Mars AX3, Mercury+ KX2, MitySOM | Specifications depend on revision and part number | Comparable values for available 3.3 V GPIOs across all variants have not been established |

## 4. Comparative Advantages and Limitations

Narvi S7. Pros: 130 I/O according to the manufacturer, published schematics and GPIO tables, integrated USB-JTAG interface and power supply circuits. Cons: the connector exposes banks operating at different voltages, including 1.5 V and 3.3 V in the documented V2.0 schematic. The module is relatively expensive and uses large multi-pin connectors.

TE0712-03-42I36-A. Pros: Artix-7 FPGA with 90 DSP48E1 blocks, 1,800 Kbit BRAM and XADC, 1 GB DDR3, Si5338 clock generator and three board-to-board connectors. Cons: I/O bank supplies must be provided by the carrier PCB. Connector routing is dense and the documentation must match the exact module assembly.

TEG2000-01-A1I-1A. Pros: GateMate A1 with an open-source HDL toolchain, four PLLs, 16 MB QSPI Flash, onboard regulators and compact board-to-board connectors. Cons: native FPGA I/O does not support direct 3.3 V operation. Only some module signals are level-shifted, so additional translators are necessary for two standard 3.3 V Pmods and the other peripherals.

Sechzig ML1. Pros: ECP5-45F FPGA, compact 60-pin edge connector, open design files and Yosys/nextpnr support. Cons: power and service connections occupy part of the 60 contacts, leaving fewer GPIOs than the connector pin count. The available peripheral signals are constrained by the edge connector.

Sechzig ML2. Pros: ECP5-45F FPGA, compact edge connection, published design files and an open-source HDL workflow. Cons: the connector has limited contacts for user signals and the peripheral mapping depends on the ML2 revision. Power and service contacts cannot be counted as GPIOs.

iCESugar-Pro. Pros: 106 GPIOs according to the project documentation, 32 MB SDRAM, 32 MB SPI Flash, onboard iCELink programmer, USB-C and an open-source HDL toolchain. Cons: the SO-DIMM 200 connector occupies substantial carrier PCB space and requires an appropriate socket and retention arrangement. The final pin mapping must respect the module's I/O banks.

SoldierCrab R3. Pros: ECP5-25F, compact M.2 E-key connection and published source materials. Cons: 47 GPIOs are fewer than the 50 independent signals in the base design budget. The module therefore cannot accommodate that exact interface allocation without external expansion or reducing the number of direct FPGA connections.

Tang Primer 20K Core. Pros: Gowin GW2A FPGA, DDR3, configuration Flash and an available development Dock. Cons: SO-DIMM 204 connection, different published counts of accessible signals and dependence on Gowin EDA for the documented development workflow.

Cmod A7-35T. Pros: Artix-7 FPGA, onboard USB-JTAG, QSPI Flash, clock source and readily accessible DIP and Pmod connections. Cons: fewer accessible signals than a dedicated high-pin-count SoM. Its breadboard-oriented form factor restricts connector placement on a custom educational carrier.

Cmod S7. Pros: Spartan-7 FPGA, USB-JTAG, configuration Flash and accessible DIP and Pmod connections. Cons: the 32 DIP digital I/O signals and additional Pmod connections impose a tighter peripheral budget. The module's prototyping format offers less freedom for carrier PCB integration.

Neso A7. Pros: Artix-7 XC7A100T, 140 published I/O signals, USB/JTAG programming and onboard support circuits. Cons: dimensions, cost and multi-pin header placement have to be accommodated on the carrier PCB.

Skoll K7. Pros: Kintex-7 XC7K70T, 150 published I/O signals, USB/JTAG programming and onboard support circuits. Cons: module dimensions, cost and connector layout increase the complexity of integrating an educational carrier PCB.

TE0873. Pros: board-to-board architecture and FPGA module infrastructure with onboard support components. Cons: the FPGA resources, exposed I/O and memory differ by part number. The listed family cannot be evaluated as a single fixed hardware configuration.

Mars AX3. Pros: Artix-7-based module family, SO-DIMM connection and configurable memory options. Cons: the exact FPGA, memory and exposed I/O count depend on the selected variant. The SO-DIMM carrier connection adds mechanical constraints.

Mercury+ KX2. Pros: Kintex-7-based module family, board-to-board connection and high I/O capacity in some variants. Cons: connector density, price and the exact available I/O depend on the module variant.

MitySOM Cyclone 10. Pros: Intel Cyclone 10 module variants with onboard memory and configuration support. Cons: LP and GX variants differ significantly, including FPGA resources, I/O counts and module connectors. The particular part number is needed for a direct comparison.

## 5. Cost and Availability

| Module | Price as of the observation date | Date | Source |
|---|---|---|---|
| iCESugar-Pro with Ext-Board | 60 USD plus 8 USD shipping to the Czech Republic, VAT not included | 10.11.2026 | [Tindie](https://www.tindie.com/products/johnnywu/icesugar-pro-fpga-development-board/) |
| SoldierCrab R3 | Price not listed. Currently unavailable | 25.11.2026 | [Electromaker](https://www.electromaker.io/shop/product/extra-soldier-crab-r3-fpga-som-to-connect-with-tiliqua-and-use) |
| Sechzig ML1 | 129.95 EUR, backordered as of the date of this report | 22.11.2026 | [Machdyne ML1](https://machdyne.com/product/sechzig-ml1-compute-module/) |
| Sechzig ML2 | 139.95 EUR, backordered as of the date of observation | 22.11.2026 | [Machdyne ML2](https://machdyne.com/product/sechzig-ml2-compute-module/) |
| Narvi S7 | 199.99 USD, shipping and tax not included | 22.11.2026 | [Numato](https://numato.com/product/narvi-spartan-7-fpga-module/) |
| TEG2000 | 75 GBP, exact offer details and taxes not confirmed | 22.11.2026 | [Trenz TEG2000](https://www.trenz-electronic.de/en/FPGA-module-with-GateMate-A1-from-Cologne-Chip-16-MByte-QSPI-Flash-4-x-5-cm/TEG2000-01-A1I-1A) |
| TE0712-03-42I36-A | No comparable price available as of the date of the study | 22.11.2026 | [Trenz TE0712](https://wiki.trenz-electronic.de/display/PD/TE0712+Resources) |

## 6. Technical Documentation

| Module | Manual and Pinout | Schematic | Purchase Page |
|---|---|---|---|
| Narvi S7 | [Manual and Pinout](https://numato.com/docs/narvi-spartan-7-fpga-module/) | [Manufacturer's Documentation](https://numato.com/docs/narvi-spartan-7-fpga-module/) | [Numato](https://numato.com/product/narvi-spartan-7-fpga-module/) |
| TE0712-03-42I36-A | [TE0712 TRM](https://wiki.trenz-electronic.de/display/PD/TE0712+TRM) | [Schematic Rev. 03, Build 42I36-A](https://www.trenz-electronic.de/trenzdownloads/Trenz_Electronic/Modules_and_Module_Carriers/4x5/TE0712/REV03/Documents/SCH-TE0712-03-42I36-A.PDF) | [Trenz Catalog](https://wiki.trenz-electronic.de/display/PD/Current+Trenz+Electronic+Shop+Articles) |
| TEG2000-01-A1I-1A | [TEG2000 TRM](https://wiki.trenz-electronic.de/display/PD/TEG2000+TRM) | [Trenz Resources](https://wiki.trenz-electronic.de/display/PD/TEG2000+Resources) | [Trenz, exact part number](https://www.trenz-electronic.de/en/FPGA-module-with-GateMate-A1-from-Cologne-Chip-16-MByte-QSPI-Flash-4-x-5-cm/TEG2000-01-A1I-1A) |
| Sechzig ML1 and ML2 | [Project Documentation](https://github.com/machdyne/sechzig) | [KiCad, GitHub](https://github.com/machdyne/sechzig) | [ML1](https://machdyne.com/product/sechzig-ml1-compute-module/), [ML2](https://machdyne.com/product/sechzig-ml2-compute-module/) |
| iCESugar-Pro | [Description and pinout](https://github.com/wuxx/icesugar-pro) | [Project Schematics](https://github.com/wuxx/icesugar-pro) | [Tindie](https://www.tindie.com/products/johnnywu/icesugar-pro-fpga-development-board/) |
| SoldierCrab R3 | [Description and Pinout](https://github.com/apfaudio/soldiercrab) | [Project Schematics](https://github.com/apfaudio/soldiercrab) | [Electromaker](https://www.electromaker.io/shop/product/extra-soldier-crab-r3-fpga-som-to-connect-with-tiliqua-and-use) |
| Tang Primer 20K Core | [Sipeed Wiki](https://wiki.sipeed.com/hardware/en/tang/tang-primer-20k/primer-20k.html) | [Sipeed Wiki](https://wiki.sipeed.com/hardware/en/tang/tang-primer-20k/primer-20k.html) | [Sipeed](https://wiki.sipeed.com/hardware/en/tang/tang-primer-20k/primer-20k.html) |
| Cmod A7 | [Digilent Documentation](https://digilent.com/shop/cmod-a7-35t-breadboardable-artix-7-fpga-module/) | [Digilent Resource Center](https://digilent.com/reference/programmable-logic/cmod-a7/start) | [Digilent](https://digilent.com/shop/cmod-a7-35t-breadboardable-artix-7-fpga-module/) |
| Cmod S7 | [Digilent Documentation](https://digilent.com/shop/cmod-s7-breadboardable-spartan-7-fpga-module/) | [Digilent Resource Center](https://digilent.com/reference/programmable-logic/cmod-s7/start) | [Digilent](https://digilent.com/shop/cmod-s7-breadboardable-spartan-7-fpga-module/) |
| Neso A7 and Skoll K7 | [Numato Documentation](https://numato.com/docs/) | [Numato Documentation](https://numato.com/docs/) | [Neso](https://numato.com/product/neso-artix-7-fpga-development-board), [Skoll](https://numato.com/product/skoll-xilinx-kintex-7-usb-ready-to-go-fpga-module) |
| TE0873 | [Trenz Resources](https://wiki.trenz-electronic.de/display/PD/TE0873+Resources) | [Trenz Resources](https://wiki.trenz-electronic.de/display/PD/TE0873+Resources) | Exact part number not specified |
| Mars AX3 and Mercury+ KX2 | [Enclustra Modules](https://www.enclustra.com/en/products/fpga-modules/) | [Enclustra Documentation](https://www.enclustra.com/en/products/fpga-modules/) | Family page, not a specific part number |
| MitySOM Cyclone 10 | [Critical Link](https://www.criticallink.com/) | [Critical Link](https://www.criticallink.com/) | Exact part number not specified |
