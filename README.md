# TLB Hit / Miss Analyser & Interactive Simulator

> A clean, interactive educational simulator for Translation Lookaside Buffer (TLB) hit/miss analysis, address translation flow, and Effective Access Time (EAT).  
> Developed for **Semester 3 Computer Engineering Operating Systems Coursework** at **Shah & Anchor Kutchhi Engineering College (SAKEC)**.

 **Live Web Application:** [https://jashjain-1.github.io/tlb-hit-miss-analyser/](https://jashjain-1.github.io/tlb-hit-miss-analyser/)

---

## Key Features & Highlights

- **Pure, Focused Simulator:** Zero extraneous bloat. Native `<select>` dropdown controls for TLB capacity, replacement policy, page size, hardware latency, workload presets, playback speed, and reference interpretation.
- **Standard Reference Benchmark:** Comes pre-loaded with the standard benchmark reference sequence:  
  `1, 2, 3, 1, 2, 4, 1, 2, 5, 1` (with verified Page Table mappings: Page 1 &rarr; Frame 5, Page 2 &rarr; Frame 7, Page 3 &rarr; Frame 2, Page 4 &rarr; Frame 9, Page 5 &rarr; Frame 4).
- **Dual Visualisation (Bar Chart & Running Trajectory):**
  1. **Hit / Miss Count Bar Chart:** Clean comparative histogram of TLB hits vs misses.
  2. **Running Hit Ratio Trajectory Graph:** Live SVG coordinate plot (0.0 to 1.0) showing how hit ratio evolves with every reference in the trace.
- **Address Translation Flow:** Live animation showing Virtual Address decomposition (`VPN` &middot; `Offset`), TLB tag search, Page Table access on miss, and Physical Address generation ($PA = PFN \times \text{PageSize} + \text{Offset}$).
- **Page-Table Accesses Counter:** Explicitly reports page-table accesses as a distinct cost separate from TLB lookups.
- **Live Effective Access Time (EAT):** Real-time latency calculation using:
  $$EAT = H \times (T + M) + (1 - H) \times (T + 2M)$$
  *(Default: $T = 10\text{ ns}$, $M = 100\text{ ns}$)*.

---

## Verified Benchmark Results (Standard Reference Benchmark)

For the benchmark reference string `1, 2, 3, 1, 2, 4, 1, 2, 5, 1` ($T = 10\text{ ns}, M = 100\text{ ns}$):

| Policy | TLB Capacity | Hits | Misses | Hit Ratio ($H$) | Page-Table Accesses | EAT (ns) | Performance Gain vs No TLB (200 ns) |
|---|---|---|---|---|---|---|---|
| **FIFO** | 3 entries | 3 | 7 | 0.30 | 7 | 180 ns | 10% faster |
| **FIFO** | 4 entries | 4 | 6 | 0.40 | 6 | 170 ns | 15% faster |
| **LRU** | 3 entries | 5 | 5 | 0.50 | 5 | 160 ns | 20% faster |
| **LRU** | 4 entries | 5 | 5 | 0.50 | 5 | 160 ns | 20% faster |

---

## How to Run Locally

Built entirely with **Vanilla HTML, CSS, and JavaScript** — no Node.js runtime, build tools, backend, or API keys required.

1. Clone this repository:
   ```bash
   git clone https://github.com/jashjain-1/tlb-hit-miss-analyser.git
   cd tlb-hit-miss-analyser
   ```

2. Open `index.html` directly in your browser:
   - **Windows:** Double-click `index.html` or run `Start-Process index.html` in PowerShell.
   - **macOS / Linux:** `open index.html` or `xdg-open index.html`.

---

## Project Team & Academic Credits

**Shah & Anchor Kutchhi Engineering College (SAKEC)**  
Department of Computer Engineering &middot; Operating Systems (Semester 3)  
Academic Year: 2026–27

- **Jash Jain** &mdash; SYCM1 &mdash; Roll No. 22 &mdash; PRN `125BTCM1106`
- **Ridham Jain** &mdash; SYCM1 &mdash; Roll No. 23 &mdash; PRN `125BTCM1159`
- **Under the Guidance of:** Prof. Vaishali Kosambkar
