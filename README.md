# Performance Analysis of Low-Power Power-on-Reset Circuit using SKY130 PDK Technology

This repository presents an analysis and design of a low-power Power-on-Reset (POR) circuit using eSim, Ngspice and SKY130 PDK technology. 

## Contents
- [Overview](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Overview)
- [Circuit Design](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Circuit-Design)
  - [Components](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Components)
- [Implementation](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Implementation)
- [Block Diagram of the POR Circuit](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Block-Diagram-of-the-POR-Circuit)
- [Circuit Diagram of the POR Circuit](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Circuit-Diagram-of-the-POR-Circuit)
- [Pre-Layout Performance Characteristics](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Pre-Layout-Performance-Characteristics)
- [Open Source Tools Used](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Open-Source-Tools-Used)
  - [eSim](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#eSim)
  - [Ngspice](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Ngspice)
  - [Skywater SKY130 PDK](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Skywater-SKY130-PDK)
- [Future Work](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Future-Work)
- [Contributors](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Contributors)
- [Acknowledgements](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Acknowledgements)
- [Contact Information](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Contact-Information)

## Overview
Power-On Reset (POR) circuits are commonly used in various electronic systems to ensure that components start up in a defined, predictable state. When an IoT device is first powered on, it needs a well-defined reset signal to ensure that all internal components start from a known state. POR circuits generate this reset signal, which is crucial for initializing the system reliably and avoiding potential issues like data corruption or unstable operation.

Traditional designs often consume significant power due to bandgap reference architectures. Here, we propose an alternative using a current reference and comparator architecture that reduces power overhead while enhancing performance and resilience against brown-out events.

## Circuit Design
Conventional Power-On Reset (POR) circuits tend to use more power due to their reliance on bandgap reference architectures, which draw current continuously to keep a stable reference voltage.

To address these challenges, we propose an alternative POR design that leverages a current reference and comparator-based architecture. This design reduces the overall power consumption of the POR circuit by eliminating the need for a bandgap reference, instead using a more efficient reference current. 

The comparator continuously monitors the supply voltage (VDD) and initiates a reset when VDD surpasses the predefined trip voltage (VPOR). This setup cuts down on power use and responds quickly and accurately during power-up.

This approach not only saves power but also improves resilience against voltage fluctuations, such as brown-out events, which could otherwise lead to unreliable operation.

### Components

1. Reference Current Generation: Sub-threshold currents through specific NMOS transistors generate a stable reference current.
2. Comparator: The reference current is compared to a tracking current from VDD to determine the reset conditions.
3. Inverter for Reset Signal: Inverters generate a reset signal, ensuring correct reset operation during power fluctuations.

## Block Diagram of the POR Circuit

![Block Diagram of the POR Circuit](https://github.com/user-attachments/assets/86eea463-e1f6-4365-99d7-504f0db5ec07)

## Circuit Diagram of the POR Circuit

![Schematic](https://github.com/user-attachments/assets/d1806c98-a36b-473a-b545-c94c71728e9b)

## Implementation
This POR circuit uses a 10-transistor configuration, integrating components like current mirrors and inverters for effective low-power operation.

- Current Mirrors: Formed by PMOS and NMOS pairs to replicate reference currents.
- Power Supply Voltage Tracking: Monitored through an NMOS transistor directly connected to VDD.
- Reset Signal (RSTN): An inverter outputs the RSTN signal, activated during power-up and brown-out events, ensuring a reliable POR function.

The design was simulated using the open-source SKY130 PDK, eSim and Ngspice.

## Pre-Layout Performance Characteristics

### VDD vs. Time [0ms - 30 ms] @ VDD = 1 V
![V(VDD)](https://github.com/user-attachments/assets/21433269-46d9-4c88-83d4-d742ddfa4650)

### V1 vs. Time [0ms - 30 ms] @ VDD = 1 V

![V(V1)](https://github.com/user-attachments/assets/5d051642-18f6-4eb7-806c-316a72ab3892)

### V2 vs. Time [0ms - 30 ms] @ VDD = 1 V

![V(V2)](https://github.com/user-attachments/assets/6d4c8da1-99b0-4a08-b073-52c487f525f5)

### RSTN vs. Time [0ms - 30 ms] @ VDD = 1 V

![V(RSTN)](https://github.com/user-attachments/assets/ba77da62-b9b0-4737-9a78-8a1cd30544ef)

### I(REF) vs. Time [0ms - 30 ms] @ VDD = 1 V

![I(IREF)](https://github.com/user-attachments/assets/3ce5938e-5ee4-4aa8-93d4-dc996359924e)

### I(MN1) vs. Time [0ms - 30 ms] @ VDD = 1 V

![I(NM1)](https://github.com/user-attachments/assets/b6c6598b-d170-45ef-9317-d849cb489e73)

### VDD vs. Time [0ms - 30 ms] @ VDD = 0.5 V

![V(VDD)](https://github.com/user-attachments/assets/0e55fec4-6d27-48a1-9b03-bede281b283f)

### V1 vs. Time [0ms - 30 ms] @ VDD = 0.5 V

![V(V1)](https://github.com/user-attachments/assets/c02c1629-8ad7-43e7-8470-76ce4a389cd6)

### V2 vs. Time [0ms - 30 ms] @ VDD = 0.5 V

![V(V2)](https://github.com/user-attachments/assets/0d8abe06-9128-44f8-b6d1-33d9244648f1)

### RSTN vs. Time [0ms - 30 ms] @ VDD = 0.5 V

![V(RSTN)](https://github.com/user-attachments/assets/21868042-80f4-4087-95db-18036fb907ff)

### I(REF) vs. Time [0ms - 30 ms] @ VDD = 0.5 V

![I(IREF)](https://github.com/user-attachments/assets/22299da5-f4cf-4a2e-9c5a-a20fd0e1d31d)

### I(NM1) vs. Time [0ms - 30 ms] @ VDD = 0.5 V

![I(NM1)](https://github.com/user-attachments/assets/b2b97ef6-a992-4ea5-9e93-8f1d84e2e4b4)

## Open Source Tools Used
### eSim

  - eSim (previously known as Oscad / FreeEDA) is a free/libre and open source EDA tool for circuit design, simulation, analysis and PCB design. It is an integrated tool built using free/libre and open source software such as KiCad, Ngspice and GHDL. eSim is released under GPL.
  - https://esim.fossee.in/home
  
### Ngspice

  - ngspice is the open source spice simulator for electric and electronic circuits.
  - http://ngspice.sourceforge.net/

### SkyWater SKY130 PDK

  - The SkyWater SKY130 PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at SkyWater’s facility.
  - https://github.com/google/skywater-pdk

## Installation of Tools
### Installation on Windows
### Installation on Ubuntu

## Future Work
- Design a variant of the circuit with more transistors (e.g., 14 or more) to support higher supply voltages while maintaining low power consumption.
- Explore the performance of the proposed circuit in smaller technology nodes to evaluate its scalability and effectiveness at lower power levels.
- Investigate improvements in brown-out detection accuracy and power consumption.
- Study the circuit's behavior under varying temperature conditions to ensure reliable operation in diverse environmental settings.

## Contributors
- Sree Vishnu Varthini S, Pre-Final Year Student, Sri Eshwar College of Engineering, sreevishnuvarthini@gmail.com

## Acknowledgements
- Mr. Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.
- Mr. Sumanto Kar, Assistant Project Manager, FOSSEE
- Dr. Maheswari Raja, Dean Innovations, Rajalakshmi Institute of Technology
- Mr. Saravanan M, Assistant Professor and Head of System On Chip - Center of Excellence, Sri Eshwar College of Engineering

## Contact Information
- Sree Vishnu Varthini S, Pre-Final Year Student, Sri Eshwar College of Engineering, sreevishnuvarthini@gmail.com
- Mr. Sumanto Kar, Assistant Project Manager, FOSSEE, sumantokar@iitb.ac.in
- Mr. Kunal Ghosh, Director, VSD Corp. Pvt. Ltd., kunalpghosh@gmail.com
- Dr. Maheswari Raja, Dean Innovations, Rajalakshmi Institute of Technology, maherajasadhana@gmail.com
- Mr. Saravanan M, Assistant Professor and Head of System On Chip - Center of Excellence, Sri Eshwar College of Engineering, saravanan.m@sece.ac.in
