# RISC-V-tapeout-Program-Week-2
Forwarding to the RISC-V , Lets's move to the WEEK 2 titled as "BabySoC Fundamentals & Functional Modelling". Week 2 is a research week whose objective is to build solid understanding of SoC fundamentals and practice functional modelling of the BabySoC using simulation tool  (Icarus verilog & GTKWave).

### Fundamentals of SoC
System on Chip (SoC) integrates a complete electronic system including processors, memory and peripherals onto a single silicon chip to reduce size, cost and power consumption. SoCs are highly specialized and now are being developed for specific applications such as enchancing machine learning, advanced AI capabilities and high-performance cloud computing with faster data processing.

### Components of SoC

* Multiple Cores: A processor with multiple cores in the form of a microcontroller, microprocessor, digital signal processor, or application-specific instruction set processor.
  
* Memory Capabilities: Memory capabilities such as RAM, ROM, FLASH, EEPROM, and/or cache memory.

* External Interfaces: External interfaces for wired communication protocols such as HDMI, USB4, FireWire, USART, SPI, I²C, or Ethernet.

* Wireless Capabilities: Wireless capabilities such as WiFi or Bluetooth and other radio frequency capabilities.

* GPU: A Graphical Processing Unit (GPU) for accelerating specific tasks and to visualize the interface.

* Voltage Regulation: Voltage regulators, phase lock loop (PLL) control systems, built-in oscillators, timers, and analog-to-digital (ADC) converters.

* Intrachip Communication: Intrachip communication subsystems for connecting individual circuit blocks, such as Interface busses or newer intercommunication networks known as networks-on-chip (NoC).

* Signal Processing: Digital, analog, and mixed-signal processing circuit blocks for any sensors, actuators, data collection, and data analysis.

### Fundamentals of BabySoC

BabySoC is a simple System-on-chip (SoC) design which is used for learning and prototyping. It includes the essential blocks of a real SoC, making it easy for design and verification.

       # Components of BabySoC includes:

       (a) Processor: It is the brain of SoC which executes instructions and control the program flow. for example: RISC-V (rvmyth)

       (b) Memory

       (c) Bus interconnect

       (d) Peripherals like UART for serial communication, GPIO, timer/counter.

       (e) Clock & Reset system for providing the operating clock for synchronous operation.

BabySoC is important for the practical introduction to SoC design. It is considered as simplified model for learning SoC concepts as it takes the complex structure ofa real SoC and reduce it to only the essential elements. 

Example: The VSDBabySoC is a simple SoC (System-on-Chip) design incorporating a RISC-V processor (rvmyth), a PLL (Phase-Locked Loop) module (pll), and a DAC (Digital-to-Analog Converter) module (dac).

### Functional Modelling

Functional modelling is the process of creating an abstract representation of a system that describes what the system does i.e its functionality rather than how it is physically implemented. It basically focuses on the behavior of the system, not on the physical and structure. 

For example: Functional model of SoC includes the details like CPU can read/write to memory, peripherals respond to the memory-mapped registers etc.

Functional modelling is done before RTL and physical design to determine whether the system work as per the intended design rather than direct physical implementation. It also validates the different achitectures choices and used for fast simulation. Funcational modelling is like a blueprint of the design which contains the behavior of the design and helps to saves time and cost before the direct implementation.

### Lab on Functional Modelling

* Tools used: Icarus Verilog, GTKWave
  
* Project Structure:
                     
    src/include/ - Contains header files (*.vh) with necessary macros or parameter definitions.
  
    src/module/ - Contains Verilog files for each module in the SoC design.
  
    output/ - Directory where compiled outputs and simulation files will be generated.
  
* Setup and Prepare Project Directory

VSDBabySoC/
├── src/
│   ├── include/
│   │   ├── sandpiper.vh
│   │   └── other header files...
│   ├── module/
│   │   ├── vsdbabysoc.v      # Top-level module integrating all components
│   │   ├── rvmyth.v          # RISC-V core module
│   │   ├── avsdpll.v         # PLL module
│   │   ├── avsddac.v         # DAC module
│   │   └── testbench.v       # Testbench for simulation
└── output/
└── compiled_tlv/         # Holds compiled intermediate files if needed

* Module Description

         * vsdbabysoc.v (Top-level SoC module)
  
         This is the top-level module that integrates the rvmyth, pll, and dac modules.
  
         # RVMYTH: RVMYTH core is a simple RISCV-based CPU, introduced by VSD.

         # PLL: A phase-locked loop or PLL is a control system that generates an output signal whose phase is related to the phase of an input signal. PLLs are widely used for synchronization purposes, including clock generation and distribution.

         # DAC: A digital-to-analog converter or DAC is a system that converts a digital signal into an analog signal. DACs are widely used in modern communication systems enabling the generation of digitally-defined transmission signals. As a result, high-speed DACs are used for mobile communications and ultra-high-speed DACs are employed in optical communications systems.

  - Inputs:
     - reset: Resets the core processor.
     - VCO_IN, ENb_CP, ENb_VCO, REF: PLL control signals.
     - VREFH: DAC reference voltage.
  - Outputs:
     - OUT: Analog output from DAC.
     - Connections:
     - RV_TO_DAC - A 10-bit bus that connects the RISC-V core output to the DAC input.
     - CLK - The clock signal generated by the PLL.
