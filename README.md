# AI Game Reverse Engineering & Research 🎮🧠

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub heaven-hm](https://img.shields.io/badge/GitHub-heaven--hm-blue?logo=github)](https://github.com/heaven-hm)
[![Author IGI Proz](https://img.shields.io/badge/Author-IGI%20Proz-green)](mailto:igiproz.hm@gmail.com)
[![Status Documentation](https://img.shields.io/badge/Docs-Markdown%20Knowledge%20Base-orange)]()

A curated open-source research repository, methodology guide, and knowledge base dedicated to **AI-assisted Video Game Reverse Engineering**, decompilation workflows, binary file format reconstruction, memory forensics, and classic game engine preservation.

Maintained by **IGI Proz / Heaven-HM** ([igiproz.hm@gmail.com](mailto:igiproz.hm@gmail.com)).

---

## 📖 Overview

Modern game reverse engineering combines classical binary analysis (static disassembly, dynamic debugging, memory hooking) with modern AI agentic workflows and Large Language Models (LLMs). This repository serves as a centralized collection of documentation and research notes covering:

1. **AI-Augmented Decompilation**: Prompt engineering, context injection, and structural recovery from raw Ghidra/IDA/Radare2 pseudocode.
2. **MCP (Model Context Protocol) Integration**: Connecting AI agents directly to **Ghidra**, **IDA Pro**, and **Radare2** for real-time querying, symbol renaming, and type propagation.
3. **Binary File Format Reconstruction**: Using heuristics and AI pattern matching to decode proprietary 3D models, textures, animations, archives, and level scripts.
4. **Dynamic Memory & State Forensics**: Hooking game loops, locating entities, tracking vtables, and mapping gameplay states.
5. **Bytecode & Virtual Machine Reversing**: Disassembling and interpreting proprietary game scripting engines.
6. **Game Engine Modernization**: Re-implementing legacy rendering, audio, and physics pipelines in modern C++ / C# / Vulkan / OpenGL.

---

## 🏆 Documented AI Reverse-Engineering Projects

A showcase of documented reverse-engineering and engine rebuild projects powered by AI agents (Claude Code, OpenAI Codex, IDA Pro, Ghidra, Radare2 MCPs):

| Project | Genre | Tools Used | Methodology & Highlights | Result | Time Taken |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [**OpenIGI**](https://github.com/OpenIGI/OpenIGI) (2000) | Tactical Stealth FPS | Claude Code + Codex + IDA Pro + Ghidra + Radare2 MCP | Decompiled stripped x86 engine, QVM script VM, MEF meshes, terrain LOD & AI perception via MCP agents. | Complete open-source engine reimplementation (.NET / OpenGL / Vulkan). | **1 month** |
| **Legends of Future Past** (1992) | Multiplayer Online MUD / RPG | Claude Code | Reverse-engineered proprietary scripts, GM manuals & 1996 recordings without source code. | Full Go engine + React + WebSocket + MongoDB rebuild (2,273 rooms, 1,990 items). | **One weekend** |
| **SkyRoads** (1993 DOS) | Futuristic 3D Racer / Flyer | Codex | Analyzed raw binary EXE only, disassembled code, built custom software renderer in Rust. | Working native Rust port running on modern OS. | **~6 hours** |
| **Disney Infinity 1.0** (2013) | Commercial Toys-to-Life | Claude Code (Opus) | Traced call graphs in symbol-stripped binary, found 13 character validation checks, generated binary patches. | Universal character unlock mod (unsolved for a decade). | **< 24 hours** |
| **Chromatron** (~2005) | Laser / Mirror Logic Puzzle | Claude Code + Cursor + Ghidra | Decompiled legacy WinXP / PowerPC binaries via GhidrAssistMCP to modern targets. | Native Apple Silicon + WebAssembly (Wasm) ports. | **Iterative** |
| **Weltendämmerung** (1980s C64) | Turn-based Strategy | Claude Code (Opus 4.5) | Spec-driven reverse engineering from 6502 machine code to modern web stack. | 1:1 accurate web browser port. | **3 days** |
| **Tomba!** (PS1) | 2.5D Action Platformer | Claude Code + Ghidra + PCSX-Redux | Created a MIPS-to-C++ static recompiler through an iterative agentic feedback loop. | Native Windows port with cutscenes, audio, combat & menus. | **~3 weeks** |
| **Era Online** (1999) | MMORPG (Visual Basic 6) | Claude Code | Autonomous exploration of client binary and protocol; built extraction tools and modern server. | Full resurrection of the classic 1999 MMORPG. | **Short** |

*For complete in-depth case studies on each project, read [09. Documented AI Reverse-Engineering & Rebuild Projects](docs/09_documented_ai_reverse_engineering_projects.md).*

---

## 📚 Documentation Index

The knowledge base is organized into focused Markdown guides:

### Core Reverse Engineering Methodologies
| Document | Description |
| :--- | :--- |
| [**01. Introduction to AI Reverse Engineering**](docs/01_introduction.md) | Fundamentals of game reverse engineering with LLMs and agentic assistants. |
| [**02. Static Analysis & Decompilation**](docs/02_static_analysis_and_decompilation.md) | Decompilation workflows with Ghidra, IDA Pro, symbol recovery, and type restoration. |
| [**03. Dynamic Analysis & Memory Forensics**](docs/03_dynamic_analysis_and_memory.md) | Hooking, debugging with x64dbg/Cheat Engine, signature scanning, and vtable analysis. |
| [**04. Binary File Format Reconstruction**](docs/04_file_format_reconstruction.md) | Step-by-step methodology to reverse engineer proprietary game formats and archives. |
| [**05. Bytecode & Scripting Engines**](docs/05_bytecode_and_scripting_engines.md) | Analyzing custom virtual machines, opcode dispatchers, and bytecode compilation. |
| [**06. AI Prompts & Ghidra Workflows**](docs/06_ai_prompts_and_ghidra_workflows.md) | Reusable AI prompts, MCP integrations, and automated headless Ghidra scripts. |
| [**07. Game Engine Preservation**](docs/07_game_engine_preservation.md) | Recreating source ports, modern 3D level editors, and preserving retro game assets. |
| [**08. Case Studies: Project I.G.I.**](docs/08_case_studies_project_igi.md) | Real-world deep-dives into Project I.G.I. engine internals, QVM scripting, and converters. |
| [**09. AI Rebuild Projects Showcase**](docs/09_documented_ai_reverse_engineering_projects.md) | Catalog of famous real-world game rebuilds created with Claude Code, Codex, IDA Pro & Ghidra. |

### Model Context Protocol (MCP) & Universal Reversing
| Document | Description |
| :--- | :--- |
| [**10. MCP in Reverse Engineering**](docs/10_mcp_reverse_engineering_architecture.md) | Architecture overview of connecting AI agents directly to disassemblers and debuggers. |
| [**11. Ghidra MCP Setup & Workflows**](docs/11_ghidra_mcp_setup_and_workflows.md) | Full setup, tool definitions, headless bridging, and agentic workflows with Ghidra. |
| [**12. IDA Pro MCP Setup & Workflows**](docs/12_ida_pro_mcp_setup_and_workflows.md) | IDAPython MCP server setup, Hex-Rays decompiler API, microcode analysis, and struct sync. |
| [**13. Radare2 & r2pipe MCP Workflows**](docs/13_radare2_r2pipe_mcp_workflows.md) | Headless r2pipe MCP server, CFG extraction, ESIL emulation, and binary diffing. |
| [**14. Universal AI Decompilation Prompts**](docs/14_universal_ai_decompilation_prompts.md) | Battle-tested prompt templates for 3D math, collision, ECS entity loops, and file parsers. |

---

## 🛠️ Tooling & Tech Stack

- **Disassemblers & Decompilers**: Ghidra, IDA Pro, Binary Ninja, Radare2 / Cutter.
- **Dynamic Debuggers**: x64dbg, Cheat Engine, ScyllaHide, Process Hacker, PCSX-Redux.
- **MCP Servers & AI**: Ghidra MCP Server, IDA Pro MCP, Radare2 MCP (`r2pipe`), Antigravity, Claude Code, OpenAI Codex.
- **File Format Analysis**: 010 Editor, ImHex, Kaitai Struct, Hex Fiend.
- **Modern Dev**: C++20, C#, Rust, Go, Python 3.12, Qt5/Qt6, OpenGL, Vulkan, CMake.

---

## 📄 License

Distributed under the [MIT License](LICENSE). See `LICENSE` for details.
