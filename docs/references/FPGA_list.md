
# FPGA Candidate Comparison

Project: FPGA Development Platform for Digital Systems Education    
Last checked: 09.11.2026  
Prices: CZK, excluding VAT, quantity 1  
Status: Preliminary selection, pending supervisor approval

## 1. Comparison of Individual FPGA Chips

| FPGA Model | Logic Resources | RAM | User I/O | Package | HDMI Support | Toolchain | Price (CZK) | Stock | Status |
|---|---|---|---|---|---|---|---:|---:|---|
| LFE5U-25F-7TG144C | 24,000 LUTs | 1,008 Kbit | 98 | TQFP-144 | Not verified | Yosys + nextpnr | 461.14 | 147 | Selected candidate |
| LFE5U-12F-8TG144I | 12,000 LUTs | 576 Kbit | 98 | TQFP-144 | Not verified | Yosys + nextpnr | 430.58 | 195 | Alternative |
| LFE5U-25F-6BG256C | 24,000 LUTs | 1,008 Kbit | 197 | BGA-256 | Not verified | Yosys + nextpnr | 449.78 | 75 | Alternative |
| ICE40UP5K-SG48I | 5,280 logic cells | 120 Kbit EBR + 1,024 Kbit SPRAM | 39 | QFN-48 | Not verified | Yosys + nextpnr | 240.03 | 0 | Alternative |
| ICE40HX8K-CT256 | 7,680 logic cells | 128 Kbit | 206 | BGA-256 | Not verified | Yosys + nextpnr | 427.06 | 0 | Alternative |
| XC7A35T-1CPG236C | 33,280 AMD logic cells | 1,800 Kbit | 106 | BGA-236 | Not verified | Vivado | 1,218.40 | 0 | Alternative |

Note: AMD logic cells and Lattice LUTs are not directly comparable. User I/O values represent package specifications, not verified usable pin assignments. Prices and availability reflect the listings checked on 03.11.2026.

### 1.1 Standalone FPGA: Strengths and Weaknesses

**LFE5U-25F-7TG144C (custom PCB):**
Strengths: 
-TQFP is easier to inspect and assemble than BGA.
-Flexible interface layout.
-Open-source Yosys/nextpnr design chain. 

Weaknesses: 
-Independent design of the power supply (including required core/I/O voltages), Flash, JTAG, oscillator, and high-frequency video path
-Pinout/bank verification and professional assembly or another reliable manufacturing process are required. **Historically selected components** for this application: `IS25LP064A-JBLE` (configuration Flash) and `TPS62142RGTT` (3.3 V buck)
-These **do not need to be automatically carried over** to the carrier PCB BOM of the finished FPGA module.


## 2. Ready-to-use FPGA modules

| Module | FPGA; Mounting Interface | I/O Pins | Power and Programming | Video / Pmod on its own carrier | Product Price and Estimated Price in CZK | Availability |
|---|---|---|---|---|---|---|
| **iCESugar-Pro v1.3** — [GitHub](https://github.com/wuxx/icesugar-pro) / [Tindie](https://www.tindie.com/) | `LFE5U-25F-6BG256C`; SODIMM-200 | **106 declared user I/O** (not the total number of free pins) | Dedicated RAM, Flash, clock, USB/iCELink; check the v1.3 schematic for power and SODIMM pin assignments | Requires a dedicated carrier board; HDMI via a separate transmitter or a verified GPDI path; Pmods are added to the carrier | **$60 ≈ 1,308 Kč** | Price/add to cart as of **November 6, 2026**; exact revision and stock levels have not been reconfirmed |
| **SoldierCrab R3** — [Crowd Supply](https://www.crowdsupply.com/apfaudio/tiliqua) / [schematics](https://github.com/apfaudio/soldiercrab) | `LFE5U-25F-6BG256C`; M.2 E-key, 22×22 mm | **47 GPIO** (plus separate JTAG/USB) | Carrier supplies 3.3 V; core regulators on the module; 16 MB Flash, 32 MiB RAM, 48 MHz; JTAG via carrier | [SandFlat](https://github.com/apfaudio/sandflat) — reference board with 4× 8-signal Pmod-compatible 2×6 and GPDI; does not guarantee the required resources simultaneously | **$129 ≈ 2,813 Kč** | **In stock** on Crowd Supply as of 2026-11-08; product listing available again on 2026-11-09 |
| **Sechzig ML1 / ML1.2** — [Machdyne](https://github.com/machdyne/sechzig) | ECP5-45F; 60-pin card edge | **Not equal to 60 GPIO**: pins include power, JTAG, and system/video interfaces | Proprietary system circuits; JTAG via carrier; PWRIO (2.5 / 3.3 V) and exact revision must be verified | [Chopin](https://machdyne.com/product/chopin-motherboard/) with 4× Pmod-compatible connectors; 3.3 V compliance depends on configuration | **€129.95 ≈ 3,164 Kč** | **Backorder** as of **November 6, 2026**, current stock not confirmed; ML1.1 and ML1.2 differ in X-line connections |
| **Sechzig ML2** — [Machdyne](https://github.com/machdyne/sechzig) | ECP5-45F; 60-pin card edge | Available GPIOs depend on the specific revision’s schematic | DDR3L RAM; programming via a compatible carrier; check PWRIO | Connectors and video signals—depending on the specific carrier/revision | **€139.95 ≈ 3,407 Kč** | **Backorder** as of **November 6, 2026**; current terms of sale are unconfirmed |

### 2.1 Modules: Strengths and Weaknesses



## 3. Sources

### Manufacturer Documentation

- [Lattice ECP5](https://www.latticesemi.com/Products/FPGAandCPLD/ECP5)
- [Lattice iCE40 UltraPlus](https://www.latticesemi.com/Products/FPGAandCPLD/iCE40UltraPlus)
- [Lattice iCE40](https://www.latticesemi.com/Products/FPGAandCPLD/iCE40)
- [AMD 7 Series FPGA Overview](https://docs.amd.com/v/u/en-US/ds180_7Series_Overview)
- [YosysHQ nextpnr](https://github.com/YosysHQ/nextpnr)

### DigiKey Product Listings

- [LFE5U-25F-7TG144C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-7TG144C/18137321)
- [LFE5U-12F-8TG144I](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-12F-8TG144I/18138132)
- [LFE5U-25F-6BG256C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-6BG256C/9553918)
- [ICE40UP5K-SG48I](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40UP5K-SG48I/7785190)
- [ICE40HX8K-CT256](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40HX8K-CT256/3083585)
- [XC7A35T-1CPG236C](https://www.digikey.cz/en/products/detail/amd/XC7A35T-1CPG236C/5039071)
