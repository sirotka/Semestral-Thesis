# FPGA Development Platform for Digital Systems Education

Semester Project: FPGA Platform for Teaching Digital Systems
University: Brno University of Technology (BUT), Faculty of Electrical Engineering and Communication (FEEC)
Course: BPC-DE1
Advisor: doc. Ing. Tomáš Frýza, Ph.D.
Status: Hardware research and comparison completed. The final architecture selection pending.

The goal is to design a custom printed circuit board for studying digital logic: the basic I/O components are located on the board, expansion modules are connected via Pmod, and the video output is removable.

## Development Process

We began work on the platform by researching existing FPGAs and FPGA modules (SoMs). For comparison, we examined their hardware resources, the number of available GPIO pins, form factors, support for development tools, cost, and the availability of components.

The next step was to analyze two implementation options: developing our own printed circuit board with a separate FPGA chip or using a ready-made FPGA module on a specially designed carrier PCB. For both options, we are investigating the specifics of power supply, programming, peripheral connectivity, and pin accessibility.

At the same time, the placement and distribution of the educational peripherals are being worked out. The main board is intended to house only the most essential components, while additional LEDs, seven-segment displays, and sensors will be connected via removable modules. Special attention is being paid to the Pmod interfaces: at least two connectors must remain available for educational tasks even when the video module is connected.

At this stage, we are continuing to compare hardware solutions. Following the selection of FPGA or module in consultation with the project supervisor, we can proceed to the final pin assignment, the development of a schematic, and PCB design in KiCad.
