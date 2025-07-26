# debouncing_circuit_vhdl
# 🔘 Verilog Debouncing Circuit with Frequency Reducer

This project implements a **pushbutton debouncing circuit** using Verilog HDL. It includes a **clock divider** (`frequency_reducer`) to slow down the clock and a **D Flip-Flop** (`dff`) to sample the input, eliminating the effects of switch bouncing.

---

## 🚀 Project Highlights

- ✅ Clean sampling of pushbutton inputs
- ✅ Reduced input clock (100 MHz → slow sampling clock)
- ✅ D Flip-Flop used to stabilize noisy signals
- ✅ Simple, simulation-ready testbench included

---

## 🧱 Module Descriptions

### 📉 1. `frequency_reducer.v`
- **Inputs**: `clk_in` (100 MHz), `rst`
- **Output**: `clk_op` (slow clock)
- **Function**: Divides high-frequency clock using a counter
- **Simulation Note**: Uses `count == 10` for fast simulation (not 12 million)

### 🔁 2. `dff.v`
- **Inputs**: `d` (pushbutton), `clk_in` (slow clock)
- **Outputs**: `q`, `qbar`
- **Function**: On each rising edge of slow clock, captures `d` into `q`

### 🧪 3. `tb_debouncing_circuit.v`
- **Purpose**: Testbench for the entire setup
- **Includes**:
  - Clock generation (`clk_in`)
  - Reset and button stimulus (`d`)
  - Output monitoring (`q`, `qbar`, `clk_op`)
  - Displaying waveforms for debugging

---

## ⚙️ How the Circuit Works

1. `clk_in` is toggled every 5 ns (100 MHz)
2. `frequency_reducer` divides this by 10 → outputs slow `clk_op`
3. `dff` samples the `d` signal on every rising edge of `clk_op`
4. `q` and `qbar` give debounced outputs

---

## 📂 File Structure

