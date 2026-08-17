# 09. Main Documented AI Reverse-Engineering & Rebuild Projects

A curated catalog of real-world, documented reverse-engineering, decompilation, and engine rebuild projects powered by AI models and agentic tools (such as Claude Code, OpenAI Codex, IDA Pro, Ghidra, Radare2 MCPs, and custom emulators).

---

## 📊 Summary Comparison Table

| # | Project | Original Era | Genre | Tools Used | Time Taken | Rebuild Result |
| :-: | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | [**OpenIGI**](https://github.com/OpenIGI/OpenIGI) (2000) | 2000 (Win32) | Tactical Stealth FPS | Claude Code + Codex + IDA Pro + Ghidra + Radare2 MCP | **1 month** | Complete open-source C#/.NET engine, QVM script VM, MEF meshes, terrain LOD, and AI perception. |
| **2** | [**Legends of Future Past**](https://github.com/jonradoff/lofp) (1992) | 1992 (CompuServe) | Multiplayer Online MUD | Claude Code | **One weekend** | Modern Go + React + WebSocket + MongoDB stack (2,273 rooms, 1,990 items, 297 monsters, 88 spells). |
| **3** | **SkyRoads** (1993 DOS) | 1993 (MS-DOS) | Futuristic 3D Racer | OpenAI Codex | **~6 hours** (Autonomous) | Full native Rust port with custom software rasterizer and authentic jump/flight physics. |
| **4** | **Disney Infinity 1.0** (2013) | 2013 (PC/Console) | Toys-to-Life Action | Claude Code (Opus) | **< 24 hours** | Universal character unlock mod bypassing 13 validation call sites (unsolved for over 10 years). |
| **5** | **Chromatron** (~2005) | 2005 (WinXP/PPC) | Laser / Mirror Puzzle | Claude Code + Cursor + Ghidra (GhidrAssistMCP) | **Iterative (Days/Weeks)** | Cross-platform native ports on Apple Silicon (macOS) and WebAssembly (Wasm browser). |
| **6** | **Weltendämmerung** (1980s) | 1980s (C64) | Turn-based Strategy | Claude Code (Opus 4.5) | **3 days** | Spec-driven reverse engineering from 6502 machine code into an authentic modern web port. |
| **7** | **Tomba!** (1997 PS1) | 1997 (PS1) | 2.5D Action Platformer | Claude Code + Ghidra + PCSX-Redux MCP | **~3 weeks** | Native Windows static recompiler port booting intro, navigation, world combat, and audio. |
| **8** | [**Era Online**](https://era-online-forever.com) (1999) | 1999 (VB6) | MMORPG | Claude Code | **Short / Low Friction** | Visual Basic 6 client & server reverse-engineered and ported to modern C# / Blazor WebAssembly. |

---

## 🔍 Detailed Game Case Studies & AI Achievements

---

### 1. OpenIGI (Project I.G.I. - 2000)

- **Genre**: Tactical Stealth First-Person Shooter / 3D Simulation
- **Original Stack**: Windows PC (DirectX 7/8, Innerloop JSF Engine, x86 Assembly, QVM Bytecode)
- **Tools Used**: **Claude Code + OpenAI Codex + IDA Pro + Ghidra + Radare2 MCP Tools**
- **Resources & Links**:
  - 🔗 **GitHub Repository**: [OpenIGI/OpenIGI](https://github.com/OpenIGI/OpenIGI)
  - 🔗 **Editor Suite**: [project-igi-editor](https://github.com/heaven-hm/project-igi-editor)
  - 🔗 **Converter & QVM Compiler**: [project-igi-converter](https://github.com/heaven-hm/project-igi-converter)
  - 🎥 **Video & Demonstrations**: [IGI Research Devs YouTube](https://www.youtube.com/@heaven-hm91)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> Multi-agent AI (Claude Code & Codex) connected to IDA Pro, Ghidra, and Radare2 MCP servers decompiled stripped x86 binaries in one month. The agents reconstructed the proprietary QVM bytecode virtual machine, MEF 3D mesh parser, continuous terrain LOD renderer, soldier AI perception raycasting, and delivered a complete open-source C#/.NET engine reimplementation.

---

### 2. Legends of Future Past (1992)

- **Genre**: Multi-User Dungeon (MUD) / Early Online Multiplayer RPG
- **Original Stack**: Proprietary 1990s server scripts & game master tools (CompuServe)
- **Tools Used**: **Claude Code**
- **Resources & Links**:
  - 🔗 **GitHub Repository**: [jonradoff/lofp](https://github.com/jonradoff/lofp)
  - 🔗 **Playable Web Client**: [lofp.metavert.io](https://lofp.metavert.io)
  - 📰 **Technical Postmortem**: [Resurrecting a 1992 MUD with Claude Code](https://metavert.io)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> Without access to original source code, creator Jon Radoff fed 1990s GM script files, manuals, and 1996 gameplay captures to Claude Code. Over a single weekend, the AI reverse-engineered the proprietary grammar, combat formulas, and monster AI, rebuilding the complete engine in Go, React, and MongoDB across 2,273 rooms and 1,990 items.

---

### 3. SkyRoads (1993 DOS)

- **Genre**: Futuristic Space Racing / Obstacle Flyer
- **Original Stack**: 16-bit x86 DOS Real-Mode binary (Creative Dimensions / BlueMoon Software)
- **Tools Used**: **OpenAI Codex / Autonomous Agent**
- **Resources & Links**:
  - 🔗 **Original Classic Game Archive**: [ClassicReload - SkyRoads](https://classicreload.com/skyroads.html)
  - 🎥 **Gameplay Reference Video**: [SkyRoads DOS Longplay](https://www.youtube.com/results?search_query=SkyRoads+1993+DOS+gameplay)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> Provided only with the raw 16-bit DOS executable `SKYROADS.EXE` and binary asset containers, Codex autonomously unpacked compressed data, disassembled x86 instructions, reverse-engineered the flight physics and jump mechanics, and synthesized a custom software rasterizer in Rust running natively on modern 64-bit operating systems in just ~6 hours.

---

### 4. Disney Infinity 1.0 (2013)

- **Genre**: Action-Adventure / Commercial Toys-to-Life
- **Original Stack**: 32-bit/64-bit Commercial PE Executable (Avalanche Software / Disney Interactive)
- **Tools Used**: **Claude Code (Opus, High Reasoning)**
- **Resources & Links**:
  - 🔗 **Community Modding Project**: [Disney Infinity Modding Research](https://github.com)
  - 📰 **Coverage & Writeups**: [Cracking 13-Year-Old Playset Restrictions with AI](https://mindstream.news)
  - 🎥 **Mod Demonstration**: [Disney Infinity All Characters Mod Video](https://www.youtube.com/results?search_query=Disney+Infinity+All+Characters+Mod)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> Facing a decade-old modding hurdle, Claude Code analyzed the stripped commercial binary without symbols. The agent mapped call graphs for `FindPlaysetForCharacter`, identified all 13 distributed validation sites that restricted characters to native playsets, and generated precise binary byte patches in under 24 hours to enable universal character freedom.

---

### 5. Chromatron (~2005–2006)

- **Genre**: Optical / Laser / Mirror Logic Puzzle
- **Original Stack**: Win32 / Classic Mac OS PowerPC (Silver Sphere Software)
- **Tools Used**: **Claude Code + Cursor + Ghidra (`GhidrAssistMCP`)**
- **Resources & Links**:
  - 🔗 **Ghidra MCP Server**: [GhidrAssistMCP](https://github.com)
  - 📰 **Technical Article**: [Vibe Decompiling: Porting a 20-Year-Old Game with Ghidra MCP](https://news.ycombinator.com)
  - 🎥 **Puzzle Gameplay**: [Chromatron Gameplay & Walkthrough](https://www.youtube.com/results?search_query=Chromatron+laser+puzzle+game)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> Using Ghidra paired with Claude Code via `GhidrAssistMCP`, developers decompiled legacy Windows XP x86 and PowerPC binaries. The agent refactored 20-year-old assembly into portable modern C++, tested multiple rendering backends (Raylib, SDL2), and delivered fully playable native ports on Apple Silicon macOS and in-browser WebAssembly.

---

### 6. Weltendämmerung (1980s C64)

- **Genre**: Turn-Based Fantasy Grand Strategy
- **Original Stack**: MOS Technology 6502 Machine Code / Commodore 64
- **Tools Used**: **Claude Code (Opus 4.5)**
- **Resources & Links**:
  - 🔗 **GitHub Repository & Web Port**: [adolfintel/weltendaemmerung](https://github.com/adolfintel/weltendaemmerung)
  - 📰 **Project Writeup**: [Spec-Driven C64 Reverse Engineering with Claude Opus 4.5](https://github.com)
  - 🎥 **C64 Gameplay Footage**: [Weltendämmerung C64 Strategy](https://www.youtube.com/results?search_query=Weltendaemmerung+C64)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> Using a spec-driven reverse engineering methodology, Claude Code disassembled 6502 machine code, translated hardware-level VIC-II graphics and memory-mapped state into formal specs, and authored a 1:1 authentic modern web implementation in just 3 days—a task that previously would have taken months of manual disassembly.

---

### 7. Tomba! (1997 PS1)

- **Genre**: 2.5D Side-Scrolling Platformer / Action-Adventure
- **Original Stack**: Sony PlayStation 1 (MIPS R3000A CPU, GTE, SPU - Whoopee Camp)
- **Tools Used**: **Claude Code + Ghidra + PCSX-Redux (Custom Debugger MCP)**
- **Resources & Links**:
  - 🔗 **Author Write-Up & Technical Blog**: [1379.tech - Static Recompiling Tomba!](https://1379.tech)
  - 🔗 **PCSX-Redux OpenBIOS**: [PCSX-Redux Project](https://github.com/grumpycoders/pcsx-redux)
  - 🎥 **Tomba! PS1 Gameplay**: [Tomba! PS1 Full Longplay Video](https://www.youtube.com/results?search_query=Tomba+PS1+gameplay+longplay)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> With zero prior console reverse-engineering experience, developer Matthew Stanley used Claude Code paired with Ghidra and a PCSX-Redux MCP server to build a MIPS-to-C++ static recompiler in 3 weeks. The resulting native Windows executable boots retail discs, plays FMV cinematics, and runs gameplay at native resolution.

---

### 8. Era Online (1999)

- **Genre**: 2D Isometric MMORPG
- **Original Stack**: Microsoft Visual Basic 6 (VB6 / P-Code / Winsock API)
- **Tools Used**: **Claude Code**
- **Resources & Links**:
  - 🔗 **Official Web Portal**: [Era Online Forever](https://era-online-forever.com)
  - 📰 **Modernization Overview**: [Resurrecting VB6 MMORPGs with AI Agents](https://claude.com)
  - 🎥 **Era Online Community Video**: [Era Online Gameplay Showcase](https://www.youtube.com/results?search_query=Era+Online+1999+MMORPG)

> **🎯 What Was Achieved With Agentic AI & Reverse Engineering (~50 words):**
> Claude Code autonomously explored legacy Visual Basic 6 client binaries and undocumented network packet formats. The agent authored custom extraction tools for sprite atlases and tile maps, then refactored the entire client-server codebase into a modern C# and Blazor WebAssembly architecture playable seamlessly inside modern web browsers.

---

## 💡 Key Trends & Takeaways

1. **Massive Compression of Timelines**: Reverse engineering milestones that historically required 6–18 months of tedious manual assembly tracing are now consistently accomplished in **hours to weeks**.
2. **Multi-Tool Synergy via MCP**: Connecting agentic LLMs directly to specialized backends (**IDA Pro**, **Ghidra**, **Radare2**, **PCSX-Redux**) via **Model Context Protocol (MCP)** enables real-time memory inspection, symbol renaming, and automated binary patching.
3. **Preservation of Digital Heritage**: Agentic AI bridges the gap between obsolete legacy architectures (16-bit DOS, VB6, MIPS, 6502, custom script VMs) and modern portable ecosystems (Rust, Go, C#/.NET, C++20, WebAssembly).
