# 09. Main Documented AI Reverse-Engineering & Rebuild Projects

A curated catalog of real-world, documented reverse-engineering, decompilation, and engine rebuild projects powered by AI models and agentic tools (such as Claude Code, Codex, IDA Pro, Ghidra, Radare2 MCPs, and custom debuggers).

---

## 📊 Summary Comparison Table

| # | Project | Original Platform / Era | Genre | Tools Used | Time Taken | Rebuild Result |
| :-: | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | [**OpenIGI**](https://github.com/OpenIGI/OpenIGI) (2000) | Windows PC (DirectX 7/8) | Tactical Stealth FPS | Claude Code + Codex + IDA Pro + Ghidra + Radare2 MCP | **1 month** | Complete open-source engine reimplementation (C# / OpenGL / Vulkan), QVM script VM, MEF 3D meshes, terrain LOD, AI perception & ballistics. |
| **2** | **Legends of Future Past** (1992) | Proprietary Server / MUD | Multiplayer Online RPG | Claude Code | **One weekend** | Modern Go engine + React frontend + WebSocket multiplayer + MongoDB (2,273 rooms, 1,990 items, 297 monster types, 88 spells). |
| **3** | **SkyRoads** (1993) | MS-DOS | Futuristic 3D Racer / Flyer | OpenAI Codex | **~6 hours** (Autonomous) | Full native Rust port with rebuilt software renderer and authentic physics running directly on modern OS. |
| **4** | **Disney Infinity 1.0** (2013) | Commercial PC / Console | Action-Adventure / Toys-to-Life | Claude Code (Opus, High Reasoning) | **< 24 hours** | Universal character unlock mod removing 13 binary validation locks (unsolved by community for 10+ years). |
| **5** | **Chromatron** (~2005–2006) | Windows XP / PowerPC Mac | Logic / Laser Puzzle | Claude Code + Cursor + Ghidra (GhidrAssistMCP) | **Iterative (Days/Weeks)** | Native modern multi-target ports (Apple Silicon + WebAssembly via Raylib/SDL2/C++). |
| **6** | **Weltendämmerung** (1980s) | Commodore 64 | Turn-based Fantasy Strategy | Claude Code (Opus 4.5) | **3 days** | Complete spec-driven reverse-engineered logic + full web browser port. |
| **7** | **Tomba!** (1997) | Sony PlayStation 1 (PS1) | 2.5D Platformer / Action | Claude Code + Ghidra + PCSX-Redux (Custom MCP) | **~3 weeks** | Native Windows static recompiler port booting intro, navigation, world combat, and audio. |
| **8** | **Era Online** (1999) | Windows (Visual Basic 6) | MMORPG | Claude Code | **Short / Low Friction** | Autonomous exploration, custom tooling creation, and full resurrection to modern stack. |

> **Note**: These documented cases demonstrate the incredible synergy between agentic coding assistants (**Claude Code**, **Codex**) and disassemblers (**IDA Pro**, **Ghidra**, **Radare2**, **PCSX-Redux**) connected via **Model Context Protocol (MCP)** servers.

---

## 🔍 Detailed Project Case Studies

### 1. OpenIGI (Project I.G.I. - 2000)
- **Repository**: [OpenIGI/OpenIGI](https://github.com/OpenIGI/OpenIGI)
- **Genre**: Tactical Stealth First-Person Shooter / 3D Simulation
- **Original Stack**: Windows PC (DirectX 7/8, Innerloop JSF Engine, x86 Assembly, QVM Bytecode)
- **Tools Used**: **Claude Code + OpenAI Codex + IDA Pro + Ghidra + Radare2 MCP Tools**
- **Methodology**:
  - Full multi-agent reverse engineering of Innerloop Studios' proprietary JSF game engine.
  - Used Claude Code and Codex connected directly to **IDA Pro**, **Ghidra**, and **Radare2** via MCP tools to decompile stripped x86 machine code, map game loops, reconstruct object hierarchies, and decode proprietary file formats (`.MEF`, `.LEV`, `.TEX`).
  - Reverse-engineered the complete QVM (Quake/Quantum Virtual Machine) script interpreter and bytecode instruction set.
  - Reconstructed the terrain level-of-detail (LOD) continuous mesh engine, soldier AI perception system, raycast line-of-sight checks, weapon ballistics, audio subsystems, and level placement coordinates.
- **Outcome**:
  - Full open-source engine reimplementation in modern **C# / .NET** with multi-backend graphics (OpenGL / Vulkan), cross-platform support (Windows, Linux, macOS), complete campaign mission support, and automated regression testing.
- **Turnaround**: **1 month** (reproducing a complete commercial 3D engine that originally took years to build).

---

### 2. Legends of Future Past (1992)
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

### 3. SkyRoads (1993 DOS)
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

### 4. Disney Infinity 1.0 (2013)
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

### 5. Chromatron (~2005–2006)
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

### 6. Weltendämmerung (1980s C64)
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

### 7. Tomba! (1997 PS1)
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

### 8. Era Online (1999)
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

1. **Massive Compression of Timeline**: Projects that historically required years of tedious manual assembly tracing are consistently completed in **hours to weeks**.
2. **Multi-Agent & Tool Synergy**: The most sophisticated rebuilds (such as **OpenIGI** and **Tomba!**) combine multiple LLM agents (Claude Code, OpenAI Codex) with specialized reverse-engineering backends (**IDA Pro**, **Ghidra**, **Radare2**, **PCSX-Redux**) using MCP tools.
3. **Preservation of Digital Heritage**: AI models bridge the gap between lost proprietary legacy technologies (VB6, MIPS, 6502, custom script VMs) and modern portable software ecosystems (C#, Rust, Go, C++20, WebAssembly).
