# Logisim Basic Computer

A simple 16-bit CPU designed and simulated entirely in **Logisim**, built as a two-part university project for CSEN/CSIS 402 – Computer Organization and Systems Programming (GUC, Spring 2026). It brings together a memory unit, ALU, register file, shared bus, and a hardwired control unit into a working "basic computer" that executes a small custom program.

---

## What's inside

- 🧠 **Control unit** — sequence counter + decoders driving every load/clear/increment/select signal
- 🧮 **ALU** — add, subtract, multiply, divide, complement, transfer, and XOR
- 🚌 **Common bus** — 7-way source select shared by all registers and memory
- 💾 **Memory** — 256 × 16-bit RAM
- 📦 **Registers** — AR, PC, DR, AC, IR, TR, each with custom load/clear circuitry

---

## Register set

| Register | Role |
|---|---|
| AR | Address Register — drives memory address lines |
| PC | Program Counter |
| DR | Data Register |
| AC | Accumulator |
| IR | Instruction Register |
| TR | Temporary Register |

## ALU operations

| Code | Operation |
|---|---|
| 001 | Transfer A |
| 010 | A + B |
| 011 | A − B |
| 100 | A × B |
| 101 | A / B |
| 110 | Complement A |
| 111 | A XOR B |

## Bus select lines

| Code | Source |
|---|---|
| 001 | Memory |
| 010 | AR |
| 011 | PC |
| 100 | DR |
| 101 | AC |
| 110 | IR |
| 111 | TR |

---

## Instruction set

Format: opcode in bits 12–15, address in bits 4–11. Every instruction begins execution at **T3** (no indirect addressing).

`LDA` `STA` `ADD` `ISZ` `BUN` `DIV` `XOR`

`DIV` and `XOR` are custom additions layered onto the standard basic-computer opcodes (built on top of the unused `BSA` and `AND` slots).

## Demo program

Runs the following loop on the simulated CPU:

```c
for (i = 0; i < 3; i++) {
    A += A XOR B;
    C += A / B;
}
```

Starting values `A = 15`, `B = 5`, `C = 0` → final result **A = 101, C = 35**, verified in simulation.

---

## Built with

[Logisim](http://www.cburch.com/logisim/) — schematic capture and simulation, no other tools required.

## Repo contents

- `.circ` circuit file
- Memory dump (`.txt`)
- Report — RTLs, timing diagrams, and control signal derivations per instruction
- Team info file
