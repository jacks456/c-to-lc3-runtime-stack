# C ➜ LC‑3 with a Proper Runtime Stack (CEG 3310 — Lab 4)

> **Goal:** Translate small C functions to LC‑3 assembly **with stack frames**, demonstrating function calls, parameter passing, local variables, and return values.

Built from the Wright State University **CEG 3310** lab spec (Lab 4).

## 🎯 Learning Outcomes
- Implement a **runtime stack** on LC‑3 (frame pointer/stack pointer discipline)
- Write **prologue/epilogue** sequences (save/restore registers)
- Pass parameters via stack; return values in a convention (e.g., **R0**)
- Verify **functional equivalence** to the C reference

## 🧩 Assigned Program (spec‑aligned)
Example function set (names illustrative—match your submission):
- `MAIN` — sets up data and calls helpers
- `SUM_OF_SQUARES(arr, n)` — iterates and accumulates
- `SQUARE(x)` — returns x*x

> The lab packet requires translating provided C to LC‑3 while enforcing **stack discipline** (not ad‑hoc register passing). Keep instructor register‑use conventions if specified in your section.

## 🧰 Tools
- LC‑3 Editor/Assembler/Simulator (e.g., PennSim or lc3tools)
- Text editor (VSCode) with LC‑3 syntax highlight (optional)

## ▶️ How to Build & Run
1. Assemble the `.asm` files to `.obj`
2. Launch the LC‑3 simulator and **load** the object file(s)
3. Initialize memory (array base, `n`, etc.) per comments at top of `MAIN.asm`
4. Set the **starting address** to the entry label (e.g., `MAIN`) and **Run**

## 🧪 Expected Behavior (example)
- For `arr = [1, 3, 4]`, program stores/prints `1^2 + 3^2 + 4^2 = 26`
- Return value placed in `R0` (or as directed by the spec)
- All **callee‑saved registers restored**; SP/FP balanced on return

## 🧱 Repo Structure
```
src/
  lab04_main.asm
  lab04_sum_of_squares.asm
  lab04_square.asm
docs/
  stack-frame-diagram.png   # visual of SP/FP movement
  call-sequence.md          # notes on calling convention
README.md
LICENSE
```

## 🔧 Implementation Notes
- **Prologue**: push old FP, set FP=SP, allocate locals, save needed registers
- **Epilogue**: write return value to agreed register, restore registers, dealloc locals, pop FP, `RET`
- Respect the lab’s **parameter order and stack layout**

## ✅ Testing
- Unit‑style: invoke `SQUARE` with values (0,1,2,−3)
- Integration: run `SUM_OF_SQUARES` on several arrays
- Boundary: empty array or `n=0` (if lab permits)

## 📚 Academic Integrity
This repo contains **original assembly** and **design notes**. The lab PDF is **not** redistributed; follow your course policy for sharing solutions.
