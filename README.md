# Awesome Reverse-Engineered Games 🎮

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub heaven-hm](https://img.shields.io/badge/GitHub-heaven--hm-blue?logo=github)](https://github.com/heaven-hm)
[![Author IGI Proz](https://img.shields.io/badge/Author-IGI%20Proz-green)](mailto:igiproz.hm@gmail.com)
[![Status Documentation](https://img.shields.io/badge/Docs-Markdown%20Knowledge%20Base-orange)](docs/)

A curated list and comprehensive guide of **awesome reverse-engineered, decompiled, and rebuilt games** powered by AI models and agentic tools (Claude Code, OpenAI Codex, IDA Pro, Ghidra, Radare2 MCPs, and custom emulators).

---

## 📖 Overview

Modern game reverse engineering combines classical binary analysis (static disassembly, dynamic debugging, memory hooking) with modern AI agentic workflows and Large Language Models (LLMs). This repository serves as a centralized collection of documentation, case studies, and research notes covering:

1. **AI-Augmented Decompilation**: Prompt engineering, context injection, and structural recovery from raw Ghidra/IDA/Radare2 pseudocode.
2. **MCP (Model Context Protocol) Integration**: Connecting AI agents directly to **Ghidra**, **IDA Pro**, and **Radare2** for real-time querying, symbol renaming, and type propagation.
3. **Binary File Format Reconstruction**: Using heuristics and AI pattern matching to decode proprietary 3D models, textures, animations, archives, and level scripts.
4. **Dynamic Memory & State Forensics**: Hooking game loops, locating entities, tracking vtables, and mapping gameplay states.
5. **Bytecode & Virtual Machine Reversing**: Disassembling and interpreting proprietary game scripting engines.
6. **Game Engine Modernization**: Re-implementing legacy rendering, audio, and physics pipelines in modern C++ / C# / Vulkan / OpenGL.

---

## 🏆 Documented Reverse-Engineered Games

### Summary Matrix

| Project | Genre | Tools Used | Methodology & Highlights | Result | Time Taken |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [**OpenIGI**](https://github.com/OpenIGI/OpenIGI) (2000) | Tactical Stealth FPS | Claude Code + Codex + IDA Pro + Ghidra + Radare2 MCP | Decompiled stripped x86 engine, QVM script VM, MEF meshes, terrain LOD & AI perception via MCP agents. | Complete open-source engine reimplementation (.NET / OpenGL / Vulkan). | **1 month** |
| [**Legends of Future Past**](https://github.com/jonradoff/lofp) (1992) | Multiplayer Online MUD / RPG | Claude Code | Reverse-engineered proprietary scripts, GM manuals & 1996 recordings without source code. | Full Go engine + React + WebSocket + MongoDB rebuild (2,273 rooms, 1,990 items). | **One weekend** |
| **SkyRoads** (1993 DOS) | Futuristic 3D Racer / Flyer | Codex | Analyzed raw binary EXE only, disassembled code, built custom software renderer in Rust. | Working native Rust port running on modern OS. | **~6 hours** |
| **Disney Infinity 1.0** (2013) | Commercial Toys-to-Life | Claude Code (Opus) | Traced call graphs in symbol-stripped binary, found 13 character validation checks, generated binary patches. | Universal character unlock mod (unsolved for a decade). | **< 24 hours** |
| **Chromatron** (~2005) | Laser / Mirror Logic Puzzle | Claude Code + Cursor + Ghidra | Decompiled legacy WinXP / PowerPC binaries via GhidrAssistMCP to modern targets. | Native Apple Silicon + WebAssembly (Wasm) ports. | **Iterative** |
| [**Weltendämmerung**](https://github.com/adolfintel/weltendaemmerung) (1980s C64) | Turn-based Strategy | Claude Code (Opus 4.5) | Spec-driven reverse engineering from 6502 machine code to modern web stack. | 1:1 accurate web browser port. | **3 days** |
| **Tomba!** (PS1) | 2.5D Action Platformer | Claude Code + Ghidra + PCSX-Redux | Created a MIPS-to-C++ static recompiler through an iterative agentic feedback loop. | Native Windows port with cutscenes, audio, combat & menus. | **~3 weeks** |
| [**Era Online**](https://era-online-forever.com) (1999) | MMORPG (Visual Basic 6) | Claude Code | Autonomous exploration of client binary and protocol; built extraction tools and modern server. | Full resurrection of the classic 1999 MMORPG. | **Short** |

---

### 🕹️ Game Profiles & AI Rebuild Summaries

#### 1. [OpenIGI (Project I.G.I. - 2000)](https://github.com/OpenIGI/OpenIGI)
* **What the Game Is**: A milestone tactical stealth first-person shooter powered by Innerloop Studios' proprietary JSF flight and 3D simulation engine.
* **AI & RE Achievement**: Multi-agent AI (Claude Code & Codex) connected to IDA Pro, Ghidra, and Radare2 MCP servers decompiled stripped x86 binaries in one month. The agents reconstructed the QVM bytecode virtual machine, MEF 3D meshes, continuous terrain LOD renderer, and soldier AI perception raycasting into a full open-source C#/.NET engine reimplementation.
* **Links**: [OpenIGI Repo](https://github.com/OpenIGI/OpenIGI) · [3D Editor](https://github.com/heaven-hm/project-igi-editor) · [QVM Converter](https://github.com/heaven-hm/project-igi-converter) · [Video Showcase](https://www.youtube.com/watch?v=UaLWHrA1Vhk)

#### 2. [Legends of Future Past (1992)](https://github.com/jonradoff/lofp)
* **What the Game Is**: A pioneering 1990s commercial Multi-User Dungeon (MUD) text-based multiplayer RPG originally hosted on CompuServe.
* **AI & RE Achievement**: With original server source code lost, creator Jon Radoff fed 1990s GM script files and gameplay logs to Claude Code. In one weekend, the AI deduced the proprietary language grammar, combat formulas, and monster AI, rebuilding the full engine in Go, React, and MongoDB across 2,273 rooms.
* **Links**: [GitHub Repository](https://github.com/jonradoff/lofp) · [Play Online](https://lofp.metavert.io) · [Postmortem Article](https://metavert.io)

#### 3. SkyRoads (1993 DOS)
* **What the Game Is**: A fast-paced 3D space obstacle racing game released for MS-DOS by BlueMoon Software.
* **AI & RE Achievement**: Given only the raw 16-bit DOS executable `SKYROADS.EXE`, OpenAI Codex autonomously extracted assets, disassembled x86 instructions, reverse-engineered flight and gravity physics, and synthesized a custom software rasterizer in native Rust running on modern 64-bit operating systems in ~6 hours.
* **Links**: [ClassicReload Player](https://classicreload.com/skyroads.html) · [Gameplay Video](https://www.youtube.com/results?search_query=SkyRoads+1993+DOS+gameplay)

#### 4. Disney Infinity 1.0 (2013)
* **What the Game Is**: A commercial toys-to-life action-adventure game with physical figurines locked to specific in-game playsets.
* **AI & RE Achievement**: Claude Code analyzed the symbol-stripped commercial binary without documentation. The AI traced call graphs for `FindPlaysetForCharacter`, identified all 13 validation check sites locking characters to playsets, and generated precise binary byte patches in under 24 hours, solving a decade-old modding challenge.
* **Links**: [Modding Research](https://mindstream.news) · [Mod Demonstration](https://www.youtube.com/results?search_query=Disney+Infinity+All+Characters+Mod)

#### 5. Chromatron (~2005–2006)
* **What the Game Is**: An optical puzzle game by Silver Sphere Software involving laser beams, mirrors, filters, and prisms.
* **AI & RE Achievement**: Developers paired Ghidra with Claude Code via `GhidrAssistMCP` to decompile legacy Windows XP and PowerPC Mac binaries. The AI refactored legacy assembly into clean modern C++, producing fully playable native ports for Apple Silicon macOS and in-browser WebAssembly.
* **Links**: [Technical Article](https://news.ycombinator.com) · [Gameplay Walkthrough](https://www.youtube.com/results?search_query=Chromatron+laser+puzzle+game)

#### 6. [Weltendämmerung (1980s C64)](https://github.com/adolfintel/weltendaemmerung)
* **What the Game Is**: A classic turn-based fantasy grand strategy game developed for the Commodore 64 home computer.
* **AI & RE Achievement**: Using a spec-driven reverse engineering approach, Claude Code (Opus 4.5) disassembled 6502 machine code, converted hardware-level VIC-II graphics and memory-mapped states into abstract specifications, and generated a complete 1:1 modern web browser port in just 3 days.
* **Links**: [GitHub & Web Port](https://github.com/adolfintel/weltendaemmerung) · [C64 Gameplay Video](https://www.youtube.com/results?search_query=Weltendaemmerung+C64)

#### 7. Tomba! (1997 PS1)
* **What the Game Is**: A beloved 2.5D side-scrolling platformer/adventure game developed by Whoopee Camp for the Sony PlayStation 1.
* **AI & RE Achievement**: Developer Matthew Stanley used Claude Code with Ghidra and a PCSX-Redux MCP server to build a MIPS-to-C++ static recompiler in 3 weeks. The resulting native Windows port boots retail game assets, renders FMV cutscenes, and runs gameplay with authentic physics and audio.
* **Links**: [Technical Writeup](https://1379.tech) · [PCSX-Redux](https://github.com/grumpycoders/pcsx-redux) · [PS1 Longplay](https://www.youtube.com/results?search_query=Tomba+PS1+gameplay+longplay)

#### 8. [Era Online (1999)](https://era-online-forever.com)
* **What the Game Is**: A vintage 2D isometric multiplayer online role-playing game (MMORPG) originally built in Visual Basic 6.
* **AI & RE Achievement**: Claude Code autonomously analyzed legacy VB6 binaries and undocumented network packet streams, built extraction tools for sprites and tile maps, and refactored the entire client-server codebase into modern C# and Blazor WebAssembly running seamlessly in modern web browsers.
* **Links**: [Era Online Portal](https://era-online-forever.com) · [Modernization Overview](https://claude.com) · [Gameplay Video](https://www.youtube.com/results?search_query=Era+Online+1999+MMORPG)

---

## 📚 Documentation

For complete research guides, reverse-engineering methodologies, MCP tool setups (Ghidra, IDA Pro, Radare2), and prompt templates, explore the [**`docs/`**](docs/) directory.

---

## 🛠️ Tooling & Tech Stack

- **Disassemblers & Decompilers**: Ghidra, IDA Pro, Binary Ninja, Radare2 / Cutter.
- **Dynamic Debuggers**: x64dbg, Cheat Engine, ScyllaHide, Process Hacker, PCSX-Redux.
- **MCP Servers & AI**: Ghidra MCP Server, IDA Pro MCP, Radare2 MCP (`r2pipe`), Antigravity, Claude Code, OpenAI Codex.
- **File Format Analysis**: 010 Editor, ImHex, Kaitai Struct, Hex Fiend.
- **Modern Dev**: C++20, C#, Rust, Go, Python 3.12, Qt5/Qt6, OpenGL, Vulkan, CMake.
---

## 🚀 Companion Projects

- [**OpenIGI**](https://github.com/OpenIGI/OpenIGI) — Full open-source engine reimplementation of Project I.G.I.
- [**project-igi-converter**](https://github.com/heaven-hm/project-igi-converter) — Script compiler, decompiler, and multi-format asset conversion engine.
- [**project-igi-editor**](https://github.com/heaven-hm/project-igi-editor) — 3D level viewport and modding suite.

---

## 📄 License

Distributed under the [MIT License](LICENSE). See `LICENSE` for details.
