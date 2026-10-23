# InterbusForge Pro (v1.0.0)

### INTERBUS (IEC 61158-5-10 / EN 50254\) Sum Shift Register Protocol Studio, 16-Bit ID Code Manager, Scan Timing Calculator, & Ring Loopback Safety Auditor

[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](https://github.com/interbusforge/interbusforge-pro) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT) ![Standard](https://img.shields.io/badge/EN%2050254-Compliant-green.svg) ![Standard](https://img.shields.io/badge/IEC%2061158--5--10-Compliant-green.svg) ![Tests](https://img.shields.io/badge/Tests-10%2F10%20Passing-brightgreen.svg)

---

## What is InterbusForge Pro?

**InterbusForge Pro** is an open-core, zero-dependency engineering suite designed for automotive plant maintenance engineers, robotic tooling technicians, and industrial automation teams maintaining and retrofitting **INTERBUS (IEC 61158-5-10 / EN 50254\)** installations. It provides a complete browser-based workbench and CLI executable to simulate the closed sum shift register ring, construct Data Cycles and ID Cycles, manage 16-bit hardware ID codes and PCP 3.0 acyclic parameters, model real-time scan cycles, and audit physical ring loopback continuity.

---

## Key Capabilities

1. **Sum Shift Register Ring Builder & Dissector:**  
   - Simulates the active distributed shift register ring with simultaneous output shifting and sensor input read-in.  
   - Generates and verifies cyclic Data Cycles and Identification Cycles with hardware CRC-16 (polynomial `0x1021`, CCITT-False).  
2. **16-Bit Hardware ID Code & PCP Manager:**  
   - Encodes and decodes standardized 16-bit device ID words (Length bits 15..12, Category bits 10..8, Device Code bits 7..0).  
   - Simulates Peripherals Communication Protocol (PCP 3.0) acyclic parameter channels embedded within process words.  
3. **Deterministic Scan Cycle & Propagation Calculator:**  
   - Models total shift duration and physical propagation delays (forward \+ internal return lines in 5-conductor cable at 5 ns/m, plus SUPI ASIC latency).  
   - Supports 500 kbps (standard remote bus) and 2.0 Mbps (high-speed Generation 4\) modes.  
4. **10-Point Physical Ring & Loopback Safety Auditor:**  
   - Audits active loopback return circuit continuity, process data word capacity (\<= 256 words / 4096 I/O points), remote bus inter-station spans (\<= 400m RS-422), local bus branch limits (\<= 10m, max 8 devices), and optical fiber attenuation budgets.  
5. **Multi-Target Master Code Generator:**  
   - Pre-configured integration templates for Phoenix Contact RFC/ILC controllers (PC Worx Structured Text), Siemens S7-300/400 IBS DSC master cards, and Embedded C (SUPI 3/4 protocol ASIC firmware).  
6. **Standalone Python 3 CLI Executable:**  
   - Zero-dependency CLI tool (`interbus-cli.py`) for automated test harnesses and field validation.

---

## Directory Structure

product\_194/

├── README.md                              \# Complete product overview

├── source-code/                           \# Web application suite

│   ├── index.html                         \# 5-tab responsive workbench

│   ├── interbus-frame-engine.js           \# Shift register framing & CRC-16

│   ├── interbus-timing-calculator.js      \# Scan cycle timing model

│   ├── interbus-ring-auditor.js           \# 10-point ring safety auditor

│   ├── interbus-forge.css                 \# Industrial Phoenix green styling

│   └── app.js                             \# Interactive UI controller

├── build/                                 \# Executables & distribution

│   ├── interbus-cli.py                    \# Standalone Python 3 CLI tool (chmod \+x)

│   └── interbusforge-pro-v1.0.0.zip       \# Production distribution archive

├── documentation/                         \# Comprehensive manuals

│   ├── ARCHITECTURE.md                    \# Technical architecture & specs

│   ├── USER\_GUIDE.md                      \# Complete usage and test workflows

│   ├── MONETIZATION\_AND\_MARKETING\_PLAYBOOK.md \# Commercial strategy & pricing

│   └── PROGRESS\_REPORT.md                 \# Cycle status & metadata

└── screenshots/                           \# Visual assets & diagrams

    ├── interbus-studio-preview.svg        \# High-resolution UI mockup

    └── interbus-architecture-diagram.svg  \# Subsystem block diagram

---

## Quick Start

### Web Application

Open `source-code/index.html` in any web browser. No server required.

### Command-Line Interface

\# Calculate Hardware CRC-16

./build/interbus-cli.py crc-calc 0003 0002 3030 3131

\# Encode 16-Bit Device ID Code

./build/interbus-cli.py id-encode \--words 1 \--code 03

\# Calculate Scan Cycle Timing Budget

./build/interbus-cli.py timing-calc \--words 32 \--stations 16 \--baud 500 \--cable-m 200

\# Run Ring Safety Audit

./build/interbus-cli.py audit \--loopback \--words 48 \--seg-m 180 \--stations 28 \--local-m 6.5

---

## License

MIT Open License (c) 2026 InterbusForge Pro Contributors.