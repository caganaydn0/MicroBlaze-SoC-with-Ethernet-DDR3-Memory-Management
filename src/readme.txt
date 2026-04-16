MicroBlaze SoC with Ethernet & DDR3 Memory Management
This project demonstrates a high-performance System-on-Chip (SoC) architecture implemented on the Xilinx Artix-7 FPGA. The design integrates a MicroBlaze soft-core processor with external DDR3 SDRAM and Ethernet connectivity, creating a robust platform for network-based embedded applications.

System Architecture (Analysis of Block Design)
The architecture (as shown in the provided block diagram) consists of several high-level IP cores interconnected via the AXI4 protocol:

Processor Core: MicroBlaze 32-bit RISC CPU, configured with an Interrupt Controller (axi_intc) and Debug Module (mdm_1).

Memory Subsystem:

External DDR3: Managed by the MIG 7 Series (Memory Interface Generator) to provide high-capacity storage for LwIP buffers and application data.

Local Memory: BRAM-based local memory for low-latency instruction and data access.

Networking: AXI EthernetLite controller, providing the hardware interface for Ethernet communication (supported by the LwIP TCP/IP stack in software).

Connectivity & Debug:

AXI UARTLite: For serial console communication and debugging.

ILA (Integrated Logic Analyzer): Real-time on-chip hardware debugging for monitoring internal signals.

Infrastructure:

Clocking Wizard (clk_wiz_0): Generates multiple clock domains (200MHz for MIG, system clocks, and Ethernet reference clocks).

AXI Interconnect: Orchestrates data flow between the MicroBlaze master and multiple peripheral slaves.

 Technical Specifications
FPGA Platform: Artix-7 (Arty A7-35T)

Processor: MicroBlaze Soft-Core

Communication: Ethernet (MII/MDIO interface), UART (115200 Baud)

External RAM: DDR3 SDRAM via MIG 7-Series

Protocol Stack: LwIP (Lightweight IP) for TCP/UDP Echo services

 Key Implementation Details
Memory Mapping: The AXI Interconnect manages the memory-mapped access to the DDR3 controller, allowing the MicroBlaze to execute large programs that exceed internal BRAM limits.

Interrupt Management: An AXI Interrupt Controller is used to handle asynchronous events from the Ethernet and Timer peripherals, ensuring efficient CPU utilization.

Clock Synchronization: The clk_wiz_0 provides a synchronized 200MHz reference clock to the MIG IP to ensure stable DDR3 PHY operation.
