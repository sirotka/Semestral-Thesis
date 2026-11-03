# FPGA candidate comparison for DE1/DE2 teaching platform

**Research snapshot:** 2026-11-03 (DigiKey Czech Republic web listings; quantity 1, CZK excluding VAT).  
**Decision status:** `LFE5U-25F-7TG144C` remains **SELECTED**. All other devices are **comparison candidates only**. No component-change decision was made.

## Comparison

| Exact device | Logic capacity | Embedded RAM | User I/O in stated package | Package | HDMI-compatible output | HDL synthesis / P&R | DigiKey CZ, 1 pc excl. VAT; stock shown | Status |
|---|---:|---:|---:|---|---|---|---|---|
| **LFE5U-25F-7TG144C** | 24,000 4-LUTs | 1,008 Kbit EBR | **98** | 144-TQFP, 20 × 20 mm | **Not yet verified**: no hard SERDES; requires valid high-speed TMDS-capable pins/serializer or external transmitter | Yosys + nextpnr-ecp5 / Project Trellis | **461.14 Kč; 147 in stock** | **SELECTED (unchanged)** |
| LFE5U-12F-8TG144I | 12,000 4-LUTs | 576 Kbit EBR | 98 | 144-TQFP, 20 × 20 mm | Not verified; same general ECP5 I/O questions; less logic/BRAM | Yosys + nextpnr-ecp5 / Project Trellis | 430.58 Kč; 195 in stock | Candidate — lower logic capacity |
| LFE5U-25F-6BG256C | 24,000 4-LUTs | 1,008 Kbit EBR | 197 | 256-CABGA, 14 × 14 mm | Not verified; more pin-placement freedom, **not** evidence of compliant HDMI | Yosys + nextpnr-ecp5 / Project Trellis | 449.78 Kč; 75 in stock | Candidate — BGA assembly complexity |
| ICE40UP5K-SG48I | 5,280 logic cells (LUT4 + FF) | 120 Kbit EBR + 1,024 Kbit SPRAM | 39 | 48-QFN, 7 × 7 mm | Not verified; 39 pins inadequate for current proposed **64/72-signal** teaching allocation | Yosys + nextpnr-ice40 / IceStorm | 240.03 Kč; **0 in stock** | Candidate — GPIO insufficient |
| ICE40HX8K-CT256 | 7,680 logic cells (LUT4 + FF) | 128 Kbit EBR | 206 | 256-CABGA, 14 × 14 mm | Not verified; I/O speed/pairs and timing require separate evaluation | Yosys + nextpnr-ice40 / IceStorm | 427.06 Kč; **0 in stock** | Candidate — BGA and smaller logic |
| XC7A35T-1CPG236C | 33,280 **AMD logic cells** (not directly equal to Lattice 4-LUT count) | 1,800 Kbit BRAM | 106 | CPG236 / 238-CSBGA, 10 × 10 mm | Possible via device-specific SelectIO/serialization **only after** complete electrical and timing validation | Vivado (vendor-supported); open 7-series nextpnr flow **experimental** | 1,218.40 Kč; **0 in stock** | Candidate — price/toolchain conflict |

**Reading the resource numbers:** AMD's 33,280 *logic cells* are not the same unit as Lattice 4-input LUTs. Lattice ECP5 supplier listings also report 24,000 *logic elements*, whereas the manufacturer's family guide calls the 25F device 24,000 LUTs. Do not infer a benchmark ranking from these columns. User I/O figures are package maxima, **not validated physical pin allocation**. The latest internal architecture checkpoint uses 98 TG144 I/O and proposes 64 I/O with two Pmod or 72 with three (logical count only); Bank 8 and HDMI remain open issues.

**Supply interpretation:** DigiKey CZ is an international distributor's Czech storefront, **not proof of stock located in the Czech Republic**. Stock and prices are changing web listings, not binding quotes; reconfirm before purchase. Prices are quantity-one prices before Czech VAT and exclude shipping. For the Artix-7, some distributor category pages show conflicting older availability; the device-specific Czech detail page is used here.

## Assessment against project requirements

- **Primary educational objective:** Lattice ECP5-25F TG144 maintains substantial logic/EBR capacity, a non-BGA package and a supported open Yosys/nextpnr route, which matches the project priorities. This is a *design rationale*, not measured performance.
- **FPGA package / GPIO:** 98 nominal user I/O on TG144 do **not** prove that every interface can be connected legally. Bank-level VCCIO and dedicated configuration/clock functions must be verified from pin-function files and real constraints.
- **HDMI-compatible video:** **No candidate is recorded as electrically validated** for the required HDMI output. Bare FPGA logic resources, SERDES counts or presence of differential pins are not sufficient evidence. Direct TMDS must be tested against I/O standards, actual differential-capable pads, timing and PLL/serialization. If unsuccessful, evaluate an **external RGB-to-TMDS transmitter**, and revise GPIO budget. This is the key unresolved architectural risk.
- **Availability:** For these exact part numbers and these single-device storefront listings, ECP5 alternatives show stock, while UP5K, HX8K and Artix show no immediate stock. This observation is time-sensitive.
- **Toolchain:** Yosys + nextpnr has documented ECP5 and iCE40 backends. Vivado is the official Artix-7 workflow; the open nextpnr Xilinx 7-series backend is described as experimental. The DE1 Nexys-A7/Vivado assignment migration to ECP5 must still be agreed with the supervisor.

## Reproducible sources

### Manufacturer / project documentation

1. Lattice, [ECP5/ECP5-5G family product page and document index](https://www.latticesemi.com/Products/FPGAandCPLD/ECP5) — FPGA-DS-02012 version 3.4 listed, dated 2025-10-05.
2. [Lattice iCE40 UltraPlus Family Data Sheet, FPGA-DS-02008, Rev. 2.4 (2025)](https://www.latticesemi.com/Products/FPGAandCPLD/iCE40UltraPlus) — UP5K, SG48 39 GPIO, EBR and SPRAM.
3. Lattice, [iCE40 HX family data](https://www.latticesemi.com/Products/FPGAandCPLD/iCE40) — HX8K device family; validate exact device/package pin information.
4. AMD/Xilinx, [7 Series FPGAs Overview (DS180)](https://docs.amd.com/v/u/en-US/ds180_7Series_Overview) — Artix-7 family resources; supplier page confirms package I/O.
5. YosysHQ, [nextpnr documentation](https://github.com/YosysHQ/nextpnr) — ECP5/iCE40 support; Xilinx 7-series experimental support.

### Czech storefront listings — checked 2026-11-03

- [LFE5U-25F-7TG144C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-7TG144C/18137321)
- [LFE5U-12F-8TG144I](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-12F-8TG144I/18138132)
- [LFE5U-25F-6BG256C](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/LFE5U-25F-6BG256C/9553918)
- [ICE40UP5K-SG48I](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40UP5K-SG48I/7785190)
- [ICE40HX8K-CT256](https://www.digikey.cz/cs/products/detail/lattice-semiconductor-corporation/ICE40HX8K-CT256/3083585)
- [XC7A35T-1CPG236C](https://www.digikey.cz/en/products/detail/amd/XC7A35T-1CPG236C/5039071)

**Limitations:** Manufacturer specification tables and supplier detail pages were cross-checked via available published text. PDF-rendered visual checks could not be completed for all datasheets; the full package-specific pin matrices, HDMI-capable outputs, and supplier availability at checkout remain unverified. No design compilation, timing report or experimental results are claimed.
