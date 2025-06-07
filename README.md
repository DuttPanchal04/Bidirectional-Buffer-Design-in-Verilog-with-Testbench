# 🔄 Bidirectional Buffer in Verilog

This project demonstrates the design and simulation of a **Bidirectional Buffer** in Verilog HDL. A bidirectional buffer allows signals to flow in either direction between two ports (A and B), based on the state of a control signal (`en` - enable).  

---

## 📌 Project Description

- **Functionality**:
  - When `en = 1`: Port **A acts as input**, and Port **B becomes output**
  - When `en = 0`: Port **B acts as input**, and Port **A becomes output**

- **Interface**:
  - `A`  — `inout` (Bidirectional)
  - `B`  — `inout` (Bidirectional)
  - `en` — `input` (Enable signal)

This allows for flexible direction control of data flow, making it suitable for **bus communication**, **I/O interfaces**, and **two-way data paths** in digital systems.

---

## ⚙️ Design Details

Since **inout ports (`A` and `B`) cannot be directly assigned values** in Verilog, the design uses **internal tri-state driver variables**: `a_drive` and `b_drive`.

### 🔁 Logic Behavior

```verilog
if (en == 1) begin
    a_drive = 1'bz;         // A acts as input
    b_drive = A;            // B gets data from A
end else begin
    b_drive = 1'bz;         // B acts as input
    a_drive = B;            // A gets data from B
end

assign A = a_drive;

assign B = b_drive;
```
This modeling ensures safe bidirectional behavior in simulation without direct value assignments to inout ports.

## 🧪 Testbench & Verification
The testbench drives various test vectors to validate proper direction switching and signal integrity:

✅ Tested Conditions:

- Driving logic 1 and 0 from A → B and B → A
- Handling unknown (x) and high-impedance (z) values
- Switching direction dynamically by toggling en
- Verifying A & B behave as expected under both enable states

## 🔍 Simulation Observations:

- Direction changes are clean and consistent
- High-impedance behavior is maintained on passive side
- No contention or invalid assignments

## 🧰 Tools Used

- Language: Verilog HDL (IEEE 1364-2001 compliant)
- Simulation: EDA Playground
- Platform: Web-based (no installation required)

## 🖼️ Waveform
- The simulation waveform shows signal propagation from A to B and B to A, depending on the en value.
- Includes logic 1, 0, x, and z cases with proper tri-state behavior.

![Bidirectional Buffer in Verilog](https://github.com/user-attachments/assets/ebc924bd-03a0-47a9-ba38-60e48b4d66a6)

## 🌐 Run Online
Simulate this design directly on EDA Playground:
🔗 [https://www.edaplayground.com/x/h5Ap]

## 🧠 Applications

- Tri-state I/O buffers
- Bus transceivers
- Shared memory/data lines
- Communication between two subsystems using one data line

## 👤 Contact

- 📫 [dattpanchal2904@gmail.com]
- 🔗 [Linkedin](https://www.linkedin.com/in/dattpanchal04/)

