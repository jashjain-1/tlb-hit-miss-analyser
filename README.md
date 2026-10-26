# TLB Lab — TLB Hit / Miss Analyser & Interactive OS Simulator

> An interactive educational instrument and simulator for Translation Lookaside Buffer (TLB) hits, misses, address translation mathematics, and Effective Access Time (EAT).  
> Designed for **Semester 3 Computer Engineering Operating Systems Coursework**.

---

## Overview

In modern computer architectures, virtual memory provides memory protection and allows processes to execute without occupying contiguous physical address space. However, translating every virtual memory reference through page tables residing in main RAM introduces significant latency.

The **Translation Lookaside Buffer (TLB)** is a fast, associative hardware cache inside the Memory Management Unit (MMU) that stores recently accessed Virtual Page Number (VPN) to Physical Frame Number (PFN) translations.

**TLB Lab** visualises this process with mathematical rigor and editorial clarity:
- Trace arbitrary decimal and `0x` hexadecimal virtual memory addresses.
- Watch live address decomposition into Virtual Page Number (VPN) and Page Offset ($d$).
- Follow step-by-step visual lookups across the TLB and Page Table.
- Compare **FIFO** and **LRU** replacement policies under capacity pressure.
- Calculate real-time **Effective Access Time (EAT)** and hit/miss ratios.
- Review Viva examination questions and answers directly linked to simulation states.

---

## Features

1. **Deterministic Simulation Engine**
   - Configurable TLB capacity: 2, 3, 4, or 8 entries.
   - Configurable page size: 256 B (8-bit offset), 512 B (9-bit offset), or 1024 B (10-bit offset).
   - Configurable replacement policies: **LRU** (Least Recently Used) and **FIFO** (First-In, First-Out).
   - Configurable hardware latencies: TLB lookup time ($t$) and Main Memory access time ($m$).
   - Strict address validation supporting decimal and hex (e.g. `12`, `260`, `0x0104`).

2. **Step-by-Step Address Translation Visualisation**
   - Breakdown cards: Virtual Address, VPN, Page Offset, PFN, Physical Address ($PA$).
   - Interactive 16-bit bit-partitioning strip dynamically updating based on page size ($\log_2(\text{PageSize})$).
   - Animated visual path: `Virtual Address` $\rightarrow$ `TLB Lookup` $\rightarrow$ `Page Table on Miss` $\rightarrow$ `Physical Address`.

3. **Four Preset Demonstration Workloads**
   - **Repeated Pages (Temporal Locality):** Demonstrates subsequent TLB hits on recently accessed pages.
   - **Sequential Access (Spatial Locality):** Shows contiguous memory references falling on identical pages.
   - **Capacity Pressure (Thrashing):** Exceeds TLB capacity to observe continuous evictions.
   - **FIFO vs. LRU Divergence:** Accesses a page repeatedly, demonstrating how LRU protects hot pages while FIFO evicts them as the oldest resident.

4. **Live Statistics & Metrics**
   - Processed accesses, hit count, miss count.
   - Dynamic hit ratio ($h$) and miss ratio ($1 - h$).
   - Proportional visual hit/miss bar.
   - Step-by-step Effective Access Time (EAT) latency derivation.

5. **Integrated Execution Log**
   - Access index, VA (dec/hex), VPN, Offset, Result (HIT / MISS), PFN, PA (dec/hex), and exact hardware action.
   - Fully responsive with touch and keyboard accessibility.

6. **Viva Preparation & OS Theory Guide**
   - Clear architectural distinction between a **TLB Miss** (nanosecond hardware cache event) and a **Page Fault** (millisecond OS swap interrupt).
   - Interactive viva accordion with 3 curated questions and model answers.

---

## Mathematical Foundations

### 1. Address Translation Decomposition

Given Virtual Address $VA$ and Page Size $PageSize$:

$$\text{VPN} = \left\lfloor \frac{VA}{PageSize} \right\rfloor$$

$$\text{Offset } (d) = VA \bmod PageSize$$

Physical Address ($PA$) resolved with Physical Frame Number ($PFN$):

$$PA = (PFN \times PageSize) + Offset$$

### 2. Effective Access Time (EAT)

For a single-level page table where all referenced pages are resident in memory:

$$EAT = h \cdot (t + m) + (1 - h) \cdot (t + 2m)$$

Where:
- $h$ = Measured TLB hit ratio ($\frac{\text{Hits}}{\text{Processed Accesses}}$)
- $t$ = TLB lookup latency (default: 10 ns)
- $m$ = Main memory access latency (default: 100 ns)

---

## How to Run Locally

This application is built with **zero external dependencies**, frameworks, or build steps.

1. Clone or download this repository:
   ```bash
   git clone https://github.com/jashjain-1/tlb-hit-miss-analyser.git
   cd tlb-hit-miss-analyser
   ```

2. Open `index.html` in any modern web browser:
   - Double-click `index.html` in your file explorer, **or**
   - In terminal (Windows):
     ```powershell
     Start-Process index.html
     ```
   - In terminal (macOS / Linux):
     ```bash
     open index.html   # macOS
     xdg-open index.html # Linux
     ```

No local server, Node.js runtime, or API key is required.

---

## Project Structure

```
.
├── index.html       # Complete single-page application (HTML5, CSS3, Vanilla JS)
├── README.md        # Documentation, theory, and operational instructions
└── .gitignore       # Git ignore rules for system artifacts
```

---

## Project Credits

**Operating Systems · Memory Management Lab Project**  
Computer Engineering — Semester 3

- **Jash Jain** — Roll 22 — PRN `125BTCM1106`
- **Ridham Jain** — Roll 23 — PRN `125BTCM1159`

*Shah & Anchor Kutchhi Engineering College (SAKEC)*
