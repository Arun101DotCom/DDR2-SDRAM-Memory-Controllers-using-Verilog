# DDR2-SDRAM-Memory-Controllers-using-Verilog
A JEDEC-compliant DDR2 SDRAM Memory Controller designed for the Micron MT47H32M16. Features a 4n-prefetch architecture and an FSM-driven Transaction Processing Logic. Supports Scalar, Block, and Atomic Read/Write operations, with dedicated modules for power-up initialization, refresh management, and Ring Buffer data synchronization.


# DDR2 SDRAM Memory Controller (Micron MT47H32M16)

This repository contains the design and implementation of a high-speed DDR2 SDRAM Memory Controller. It serves as the interface between a processor system bus and the physical memory, managing the complex timing requirements of SSTL_18 signaling.

## 🏗 System Architecture
The controller is designed to manage the **Micron MT47H32M16** (512Mb) memory module. It de-couples the processor from the memory core using an asynchronous FIFO architecture and a Ring Buffer for data strobe alignment.


### Key Logic Modules:
- **Initialization Engine:** Manages the power-up sequence and EMRS (Extended Mode Register Set) programming.
- **Transaction Processing Logic (TPL):** An FSM that handles state transitions (IDLE, ACT, READ, WRITE, PRE).
- **Arbiter:** Manages priority between processor requests.

## ⚡ Technical Features
- **4n-Prefetch:** Efficiently transfers four data words per internal clock cycle.
- **Double Data Rate:** Captures data on both the rising and falling edges of the DQS strobe.
- **Support for Multiple Access Modes:**
  - **Scalar:** Single word access via Data Masking (DM).
  - **Block:** High-bandwidth sequential transfers.
  - **Atomic:** Integrated Read-Modify-Write cycles.


## 📂 Project Contents

### 📑 01_Technical Report
In-depth analysis of DDR2 timing parameters ($t_{RFC}$, $t_{RP}$, $t_{RCD}$) and memory mapping logic.

### 💻 02_Source Codes
HDL (Verilog/VHDL) implementation of the controller logic, including the FSM and FIFO buffers.


## 🛠 Usage
The controller requires the `INITDDR` signal to be asserted to begin the initialization sequence. Once the `READY` flag is high, the controller is available for memory transactions.
