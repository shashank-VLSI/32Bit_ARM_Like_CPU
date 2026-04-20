# 🧠 ARM-like Single-Cycle CPU (Verilog)

This project implements a **32-bit ARM-like single-cycle processor** using Verilog HDL. It includes a modular design with separate components for the datapath, control unit, ALU, memory, and testbench.

---

## 📌 Features

* 32-bit architecture
* Single-cycle execution
* Modular design (easy to extend/debug)
* Supports:

  * Data Processing Instructions (ADD, SUB, AND, OR)
  * Load/Store (LDR, STR)
  * Branch Instructions (B)
* Conditional execution using flags (N, Z, C, V)
* Memory initialization using `.dat` file
* Fully testable using simulation

---

## 🏗️ Project Structure

```
.
├── alu.v            # Arithmetic Logic Unit
├── adder.v          # Simple 32-bit adder
├── controller.v     # Control unit (decoder + condition logic)
├── decoder.v        # Instruction decoder
├── condlogic.v      # Conditional execution logic
├── datapath.v       # Main datapath
├── regfile.v        # Register file (R0–R15)
├── mux2.v           # 2-to-1 multiplexer
├── flopr.v          # Flip-flop register
├── flopenr.v        # Enabled register
├── extend.v         # Immediate extender
├── imem.v           # Instruction memory
├── dmem.v           # Data memory
├── cpu.v            # CPU top integration
├── top.v            # Top-level module (CPU + memories)
├── testbench.v      # Simulation testbench
├── memfile.dat      # Program instructions (hex)
```

---

## ⚙️ Architecture Overview

### 🔹 Datapath Components

* **Program Counter (PC)**
* **Register File**
* **ALU**
* **Multiplexers**
* **Immediate Extender**
* **Instruction & Data Memory**

### 🔹 Control Unit

* **Decoder**
* **ALU Control**
* **Conditional Logic (ARM-style execution)**

---

## 🧮 ALU Operations

| ALUControl | Operation |
| ---------- | --------- |
| 00         | ADD       |
| 01         | SUB       |
| 10         | AND       |
| 11         | OR        |

### ALU Flags

| Flag | Meaning  |
| ---- | -------- |
| N    | Negative |
| Z    | Zero     |
| C    | Carry    |
| V    | Overflow |

---

## 📥 Instruction Memory (memfile.dat)

Instructions are loaded in hexadecimal format.

Example:

```
E04F000F  
E2802005  
E280300C  
E2437009  
...
```

These represent ARM-like instructions executed sequentially.

---

## 🚀 How to Run Simulation

### Using ModelSim / QuestaSim

```bash
vlog *.v
vsim testbench
run -all
```

### Using Icarus Verilog

```bash
iverilog -o cpu.out *.v
vvp cpu.out
```

---

## ✅ Testbench

The testbench verifies correct execution by checking register values:

```verilog
if (dut.cpu.dp.rf.rf[5] === 32'd11)
```

✔ Expected Output:

```
Test Passed: R5 contains 11
```

---

## 🔍 Key Modules Explained

### 🔸 ALU (`alu.v`)

Performs arithmetic and logic operations and generates flags.

### 🔸 Datapath (`datapath.v`)

Handles:

* Operand selection
* ALU execution
* Register writes
* PC updates

### 🔸 Controller (`controller.v`)

Combines:

* Decoder
* Conditional execution logic

### 🔸 Conditional Logic (`condlogic.v`)

Implements ARM-style condition checking using flags.

---

## 📚 Learning Concepts Covered

* Computer Architecture
* RISC Processor Design
* Verilog HDL
* Digital Logic Design
* ARM Instruction Format
* Control & Datapath Separation

---

## 🛠️ Future Improvements

* Pipeline implementation
* Hazard detection
* More ARM instructions (MUL, CMP, etc.)
* Cache integration
* Interrupt handling

---

## 👨‍💻 Author

* Designed and implemented as part of CPU architecture learning project.

---

## 📄 License

This project is open-source and available under the MIT License.

---

## ⭐ Contribute

Feel free to fork, improve, and submit pull requests!

---

## 🙌 Acknowledgements

Inspired by:

* ARM architecture concepts
* Digital design textbooks
* Computer architecture courses

---
