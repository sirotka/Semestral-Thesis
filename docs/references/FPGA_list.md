
# FPGA Candidate Comparison

Project: FPGA Development Platform for Digital Systems Education    
Last checked: 11.11.2026  
Prices: CZK, quantity 1  
Status: Preliminary selection, pending supervisor approval

## 1. Comparison of Individual FPGA Chips

| FPGA Model | Logic Resources | RAM | User I/O | Package | HDMI Support | Toolchain | Price (CZK) |
|---|---|---|---|---|---|---|---:|
| LFE5U-25F-7TG144C | 24,000 LUTs | 1,008 Kbit | 98 | TQFP-144 | Not verified | Yosys + nextpnr | 461.14 |
| LFE5U-12F-8TG144I | 12,000 LUTs | 576 Kbit | 98 | TQFP-144 | Not verified | Yosys + nextpnr | 430.58 |
| LFE5U-25F-6BG256C | 24,000 LUTs | 1,008 Kbit | 197 | BGA-256 | Not verified | Yosys + nextpnr | 449.78 |
| ICE40UP5K-SG48I | 5,280 logic cells | 120 Kbit EBR + 1,024 Kbit SPRAM | 39 | QFN-48 | Not verified | Yosys + nextpnr | 240.03 |
| ICE40HX8K-CT256 | 7,680 logic cells | 128 Kbit | 206 | BGA-256 | Not verified | Yosys + nextpnr | 427.06 |
| XC7A35T-1CPG236C | 33,280 AMD logic cells | 1,800 Kbit | 106 | BGA-236 | Not verified | Vivado | 1,218.40 |

Note: AMD logic cells and Lattice LUTs are not directly comparable. User I/O values represent package specifications, not verified usable pin assignments. Prices and availability reflect the listings checked on 03.11.2026.

### 1.1 Standalone FPGA: Strengths and Weaknesses

**LFE5U-25F-7TG144C (custom PCB)**

Strengths: 

- TQFP is easier to inspect and assemble than BGA.
- Flexible interface layout.
- Open-source Yosys/nextpnr design chain. 

Weaknesses: 

- Independent design of the power supply (including required core/I/O voltages), Flash, JTAG, oscillator, and high-frequency video path.
- Pinout/bank verification and professional assembly or another reliable manufacturing process are required. Historically selected components for this application: IS25LP064A-JBLE (configuration Flash) and TPS62142RGTT (3.3 V buck).
- These do not need to be automatically carried over to the carrier PCB BOM of the finished FPGA module.


## 2. Comparison of ready-to-use FPGA modules

| Module | FPGA | LUT | BRAM, Kbit | External RAM | SPI Flash | GPIO | Clock | Connector | Programming | Carrier | Price (CZK) |
|---|---|---:|---:|---|---|---:|---|---|---|---|---:|
| iCESugar-Pro | ECP5-25F | 24000 | 1008 | 32 MB SDRAM | 32 MB | 106 | 25 MHz | SODIMM-200 | iCELink / USB-C | Ext-Board | 1 483 |
| Colorlight i5 v7.0 | ECP5-25F | 24000 | 1008 | 8 MB SDRAM | 2 MB | 106 | 25 MHz | SODIMM-200 | JTAG | Ext Board | 1040 |
| Colorlight i9 v7.2 | ECP5-45F | 44000 | 1944 | 8 MB SDRAM | 8 MB | 106 | 25 MHz | SODIMM-200 | JTAG | Ext Board | 1766 |
| SoldierCrab R3 | ECP5-25F | 24000 | 1,008 | 32 MB oSPI-RAM | 16 MB | 47 | 48 MHz | M.2 E-key | JTAG | SandFlat | 2813 |
| Sechzig ML1.2 | ECP5-45F | 44000 | 1944 | — | — | — | 48 MHz (carrier) | 60-pin edge | JTAG | Chopin | 3164 |
| Sechzig ML2.0B | ECP5-45F | 44,000 | 1,944 | — | — | — | 48 MHz (carrier) | 60-pin edge | JTAG | Chopin | 3407 |

### 2.1 Modules: Strengths and Weaknesses

**iCESugar-Pro (ready-to-use FPGA module)**

Strengths: 

- Built-in iCELink programmer with a USB-C connector.
- 106 GPIO pins for connecting educational peripherals and a video output.
- 32 MB of SDRAM and 32 MB of SPI flash memory.
- Open-source hardware documentation and an HDL toolkit.
- Available with an Ext-Board for testing before manufacturing a custom PCB.
- Built-in RGB LED and microSD card slot.
- Low price: approximately 1483 CZK for the module and Ext-Board.

Weaknesses:

- Large SODIMM-200 connector.
- Additional hardware development is required for HDMI output.

## 3. Comparison of Architectures and Preliminary Selection

The main difference between these two approaches is the complexity of manufacturing a specialized printed circuit board. Using a standalone FPGA requires designing all necessary support circuits, whereas a ready-made module allows the design to focus on educational peripherals and expansion interfaces.

For this project, the modular approach appears to be more practical, as it reduces the complexity of hardware development and allows for testing prior to the fabrication of a custom printed circuit board. Currently, the iCESugar-Pro module is the preferred choice due to its optimal balance of cost, number of available GPIO pins, and ease of design.

**Both the choice of architectural design and the selection of a specific module are preliminary and require supervisor approval.**

## 4. Sources

- [Lattice ECP5](https://www.latticesemi.com/Products/FPGAandCPLD/ECP5)
- [Lattice iCE40 UltraPlus](https://www.latticesemi.com/Products/FPGAandCPLD/iCE40UltraPlus)
- [Lattice iCE40](https://www.latticesemi.com/Products/FPGAandCPLD/iCE40)
- [AMD 7 Series FPGA Overview](https://docs.amd.com/v/u/en-US/ds180_7Series_Overview)
- [YosysHQ nextpnr](https://github.com/YosysHQ/nextpnr)
- [LFE5U-25F-7TG144C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-7TG144C/18137321)
- [LFE5U-12F-8TG144I](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-12F-8TG144I/18138132)
- [LFE5U-25F-6BG256C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-6BG256C/9553918)
- [ICE40UP5K-SG48I](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40UP5K-SG48I/7785190)
- [ICE40HX8K-CT256](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40HX8K-CT256/3083585)
- [XC7A35T-1CPG236C](https://www.digikey.cz/en/products/detail/amd/XC7A35T-1CPG236C/5039071)
- [iCESugar-Pro: Schematic and Specifications](https://github.com/wuxx/icesugar-pro) · [Tindie / MuseLab](https://www.tindie.com/products/johnnywu/icesugar-pro-fpga-development-board/)
- [Colorlight i5/i9: Schematics and Pinout](https://github.com/wuxx/Colorlight-FPGA-Projects)
-  [Colorlight i5 GPIO](https://tomverbeure.github.io/2021/01/22/The-Colorlight-i5-as-FPGA-development-board.html)
- [Colorlight i5/i9, AliExpress](https://www.aliexpress.com/item/1005007788475037.html)
- [iCESugar-Pro AliExpress, kit](https://www.aliexpress.com/item/1005007788574025.html)
- [FireChip](https://www.aliexpress.com/item/1005012786940475.html)
- [Fruugo](https://www.fruugo.cz/icesugar-pro-fpga-development-board-lattice-ecp5-open-source-risc-v-linux-sodimm/p-458509278-962739837)
- [SoldierCrab](https://github.com/apfaudio/soldiercrab)
- [SandFlat](https://github.com/apfaudio/sandflat)
- [Crowd Supply](https://www.crowdsupply.com/apfaudio/tiliqua)
- [Sechzig](https://github.com/machdyne/sechzig)
- [Chopin](https://machdyne.com/product/chopin-motherboard/)
- [ULX3S](https://github.com/emard/ulx3s)
- [ECPIX-5](https://shop.lambdaconcept.com/home/46-ecpix-5.html)
- [Mimas ECP5 Mini](https://numato.com/product/mimas-ecp5-mini-fpga-development-board/)
- [Icepi Zero](https://www.crowdsupply.com/icy-electronics/icepi-zero)
- [TFP410 datasheet](https://www.ti.com/lit/ds/symlink/tfp410.pdf)
- [1BitSquared video Pmod](https://1bitsquared.de/products/pmod-digital-video-interface)


