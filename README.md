# Performance Analysis of Low-Power Power-on-Reset Circuit using SKY130 PDK Technology
[Overview](https://github.com/Sree-Vishnu-Varthini/LowPowerPOR_SKY130/#Overview)

## Overview
This repository presents an analysis and design of a low-power Power-on-Reset (POR) circuit using SKY130 PDK technology. 

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

## Implementation
This POR circuit uses a 10-transistor configuration, integrating components like current mirrors and inverters for effective low-power operation.

- Current Mirrors: Formed by PMOS and NMOS pairs to replicate reference currents.
- Power Supply Voltage Tracking: Monitored through an NMOS transistor directly connected to VDD.
- Reset Signal (RSTN): An inverter outputs the RSTN signal, activated during power-up and brown-out events, ensuring a reliable POR function.

The design was simulated using the open-source SKY130 PDK.

## Block Diagram of the POR Circuit

![Block Diagram of the POR Circuit](https://github.com/user-attachments/assets/86eea463-e1f6-4365-99d7-504f0db5ec07)

## Circuit Diagram of the POR Circuit

![Schematic](https://github.com/user-attachments/assets/d1806c98-a36b-473a-b545-c94c71728e9b)
