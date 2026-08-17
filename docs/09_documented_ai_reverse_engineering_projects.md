# 09. Main Documented AI Reverse-Engineering & Rebuild Projects

A curated catalog of real-world, documented reverse-engineering, decompilation, and engine rebuild projects powered by AI models and agentic tools (such as Claude Code, Codex, Ghidra MCPs, and custom debuggers).

---

## 📊 Summary Comparison Table

| # | Project | Original Platform / Era | Genre | Tools Used | Time Taken | Rebuild Result |
| :-: | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | **Legends of Future Past** (1992) | Proprietary Server / MUD | Multiplayer Online RPG | Claude Code | **One weekend** | Modern Go engine + React frontend + WebSocket multiplayer + MongoDB (2,273 rooms, 1,990 items, 297 monster types, 88 spells). |
| **2** | **SkyRoads** (1993) | MS-DOS | Futuristic 3D Racer / Flyer | OpenAI Codex | **~6 hours** (Autonomous) | Full native Rust port with rebuilt software renderer and authentic physics running directly on modern OS. |
| **3** | **Disney Infinity 1.0** (2013) | Commercial PC / Console | Action-Adventure / Toys-to-Life | Claude Code (Opus, High Reasoning) | **< 24 hours** | Universal character unlock mod removing 13 binary validation locks (unsolved by community for 10+ years). |
| **4** | **Chromatron** (~2005–2006) | Windows XP / PowerPC Mac | Logic / Laser Puzzle | Claude Code + Cursor + Ghidra (GhidrAssistMCP) | **Iterative (Days/Weeks)** | Native modern multi-target ports (Apple Silicon + WebAssembly via Raylib/SDL2/C++). |
| **5** | **Weltendämmerung** (1980s) | Commodore 64 | Turn-based Fantasy Strategy | Claude Code (Opus 4.5) | **3 days** | Complete spec-driven reverse-engineered logic + full web browser port. |
| **6** | **Tomba!** (1997) | Sony PlayStation 1 (PS1) | 2.5D Platformer / Action | Claude Code + Ghidra + PCSX-Redux (Custom MCP) | **~3 weeks** | Native Windows static recompiler port booting intro, navigation, world combat, and audio. |
| **7** | **Era Online** (1999) | Windows (Visual Basic 6) | MMORPG | Claude Code | **Short / Low Friction** | Autonomous exploration, custom tooling creation, and full resurrection to modern stack. |

> **Note**: Most of these documented cases rely primarily on **Claude Code** or agentic coding assistants as the primary driver, frequently paired with **Ghidra** and specialized **MCP (Model Context Protocol)** servers for binary decompilation and runtime debugging.

---

## 🔍 Detailed Project Case Studies

### 1. Legends of Future Past (1992)
- **Genre**: Multi-User Dungeon (MUD) / Early Online Multiplayer RPG
- **Original Stack**: Proprietary 1990s server scripts & game master tools
- **Tools Used**: Claude Code
- **Methodology**:
  - Without access to original server source code, old custom scripts, a 1998 Game Master manual, and 1996 raw gameplay recordings were provided to the AI.
  - The agentic loop analyzed the syntax of the proprietary scripting language, reconstructed the underlying probability curves, combat damage formulas, monster AI behaviors, and item drop tables.
- **Outcome**:
  - Complete, modern full-stack rewrite in **Go** (engine backend) + **React** (frontend client) + **WebSockets** (real-time multiplayer) + **MongoDB** (database).
  - Accurate preservation of 2,273 unique rooms, 1,990 items, 297 monster archetypes, and 88 spells.
- **Turnaround**: **One single weekend**.

---

### 2. SkyRoads (1993 DOS)
- **Genre**: Futuristic Space Racing / Obstacle Flyer
- **Original Stack**: 16-bit x86 DOS Real-Mode binary
- **Tools Used**: Codex / Autonomous Agent
- **Methodology**:
  - The AI was provided *only* with the raw original binary executable (`SKYROADS.EXE`) and asset containers.
  - The agent autonomously unpacked compressed assets, disassembled x86 instructions, mapped the flight physics and jump mechanics, and synthesized a custom software rasterizer in Rust.
- **Outcome**:
  - High-performance native **Rust** port compiling and executing natively on Windows, Linux, and macOS without requiring DOSBox emulation.
- **Turnaround**: **~6 hours** of autonomous iteration.

---

### 3. Disney Infinity 1.0 (2013)
- **Genre**: Action-Adventure / Commercial Toys-to-Life
- **Original Stack**: 32-bit/64-bit Commercial PE Executable (Denuvo/DRM-era complexity)
- **Tools Used**: Claude Code (Opus, High Reasoning)
- **Methodology**:
  - Analyzed the commercial binary stripped of all debugging symbols and internal documentation.
  - Traced execution call graphs around the hardware RFID portal scanner and playset character authentication checks.
  - Successfully located 13 disparate validation check-points throughout the executable that locked specific characters to specific playsets.
  - Generated precise binary byte-level assembly patches to bypass restrictions safely.
- **Outcome**:
  - Universal Character Unlock mod enabling cross-playset character usage—a challenge that remained unsolved by the modding community for over a decade.
- **Turnaround**: **Under 24 hours**.

---

### 4. Chromatron (~2005–2006)
- **Genre**: Optical / Laser / Mirror Logic Puzzle
- **Original Stack**: Win32 / Classic Mac OS PowerPC
- **Tools Used**: Claude Code + Cursor + Ghidra (with `GhidrAssistMCP`)
- **Methodology**:
  - Extracted decompiled C code from legacy Windows XP x86 and PowerPC binaries using Ghidra connected directly to LLM tools via MCP.
  - Benchmarked multiple modern rendering architectures (Raylib, SDL2, modern C++) to identify the most portable solution.
- **Outcome**:
  - Cross-platform playable ports running natively on Apple Silicon (ARM64 macOS) and WebAssembly (Wasm) in modern web browsers.
- **Turnaround**: Iterative development over several days/weeks.

---

### 5. Weltendämmerung (1980s C64)
- **Genre**: Turn-Based Fantasy Grand Strategy
- **Original Stack**: MOS Technology 6502 Machine Code / Commodore 64
- **Tools Used**: Claude Code (Opus 4.5)
- **Methodology**:
  - Spec-driven reverse engineering methodology. The agent disassembled 6502 assembly, translated memory-mapped I/O and VIC-II graphics calls into abstract game state specifications, and generated clean idiomatic code.
  - AI wrote nearly 100% of the game engine, state management, and user interface.
- **Outcome**:
  - 1:1 authentic modern Web browser port recreating the complete game mechanics and visual aesthetics.
- **Turnaround**: **3 days** (compared to estimated weeks/months with traditional manual disassembly).

---

### 6. Tomba! (1997 PS1)
- **Genre**: 2.5D Side-Scrolling Platformer / Action-Adventure
- **Original Stack**: Sony PlayStation (MIPS R3000A CPU, GTE, SPU)
- **Tools Used**: Claude Code + Ghidra + PCSX-Redux (Custom Debugger MCP)
- **Methodology**:
  - Developed a static binary recompiler with zero prior console reverse-engineering experience.
  - Established a tight feedback loop: Decompile MIPS subroutine → Generate C++ → Compile native binary → Run in debugger → Identify graphical/logic divergence → Feed error back to Claude.
- **Outcome**:
  - Native Windows executable port that boots the game, renders FMV cutscenes, plays audio, handles pad input, and enables full world navigation and combat.
- **Turnaround**: **~3 weeks** of guided agentic iteration.

---

### 7. Era Online (1999)
- **Genre**: 2D Isometric MMORPG
- **Original Stack**: Microsoft Visual Basic 6 (VB6 / P-Code / Native)
- **Tools Used**: Claude Code
- **Methodology**:
  - Autonomous exploration workflow: Claude explored the legacy client binary and packet protocol, authored custom parsing tools to extract map tiles and sprites, and re-implemented the client-server architecture in modern languages.
- **Outcome**:
  - Complete modern resurrection of a lost 1999 MMORPG made accessible on modern operating systems and web infrastructure.
- **Turnaround**: Fast, low-friction turnaround.

---

## 💡 Key Trends & Takeaways

1. **Massive Compression of Timeline**: Projects that historically required 6–18 months of tedious manual assembly tracing are consistently completed in **hours to weeks**.
2. **The Power of Agentic Tooling + MCP**: Pairing LLMs directly with reverse-engineering environments (Ghidra, IDA, x64dbg, PCSX-Redux) via **Model Context Protocol (MCP)** enables real-time iteration, symbol inspection, and automated patching.
3. **Preservation of Digital Heritage**: AI models bridge the gap between lost proprietary legacy technologies (VB6, MIPS, 6502, custom script VMs) and modern portable software ecosystems (Rust, Go, C++20, WebAssembly).
