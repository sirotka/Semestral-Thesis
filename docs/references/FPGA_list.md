
# FPGA Candidate Comparison

Project: FPGA Development Platform for Digital Systems Education  
Course: BPC-DE1  
Last checked: 2026-11-03  
Supplier: DigiKey Czech Republic  
Prices: CZK, excluding VAT, quantity 1  
Status: Preliminary selection, pending supervisor approval

## 1. FPGA Comparison

| FPGA Model | Logic Resources | RAM | User I/O | Package | HDMI Support | Toolchain | Price (CZK) | Stock | Status |
|---|---|---|---|---|---|---|---:|---:|---|
| LFE5U-25F-7TG144C | 24,000 LUTs | 1,008 Kbit | 98 | TQFP-144 | Not verified | Yosys + nextpnr | 461.14 | 147 | Selected candidate |
| LFE5U-12F-8TG144I | 12,000 LUTs | 576 Kbit | 98 | TQFP-144 | Not verified | Yosys + nextpnr | 430.58 | 195 | Alternative |
| LFE5U-25F-6BG256C | 24,000 LUTs | 1,008 Kbit | 197 | BGA-256 | Not verified | Yosys + nextpnr | 449.78 | 75 | Alternative |
| ICE40UP5K-SG48I | 5,280 logic cells | 120 Kbit EBR + 1,024 Kbit SPRAM | 39 | QFN-48 | Not verified | Yosys + nextpnr | 240.03 | 0 | Alternative |
| ICE40HX8K-CT256 | 7,680 logic cells | 128 Kbit | 206 | BGA-256 | Not verified | Yosys + nextpnr | 427.06 | 0 | Alternative |
| XC7A35T-1CPG236C | 33,280 AMD logic cells | 1,800 Kbit | 106 | BGA-236 | Not verified | Vivado | 1,218.40 | 0 | Alternative |

Note: AMD logic cells and Lattice LUTs are not directly comparable. User I/O values represent package specifications, not verified usable pin assignments. Prices and availability reflect the listings checked on 2026-11-03.

## 2. Proposed FPGA

Device: LFE5U-25F-7TG144C  
Manufacturer: Lattice Semiconductor  
Family: ECP5

Reasons for selection:

- Open-source synthesis and place-and-route using Yosys and nextpnr.
- Sufficient logic and memory resources for the planned DE1 applications.
- 98 nominal user I/O pins.
- TQFP-144 package, easier to assemble and inspect than BGA.
- Competitive price and availability compared with the alternatives.

HDMI-compatible output remains to be verified. The selected FPGA has no dedicated SERDES in this package; an external HDMI transmitter may be required.

Final FPGA approval: Pending supervisor review.

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
