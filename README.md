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

1. **AI-Augmented Decompilation**: Prompt engineering, context injection, and structural recovery from raw Ghidra/IDA C pseudocode.
2. **Binary File Format Reconstruction**: Using heuristics and AI pattern matching to decode proprietary 3D models, textures, animations, archives, and level scripts.
3. **Dynamic Memory & State Forensics**: Hooking game loops, locating entities, tracking vtables, and mapping gameplay states.
4. **Bytecode & Virtual Machine Reversing**: Disassembling and interpreting proprietary game scripting engines (e.g. QVM/QSC in Project I.G.I.).
5. **Game Engine Modernization**: Re-implementing legacy rendering, audio, and physics pipelines in modern C++ / Vulkan / OpenGL.

---

## 📚 Documentation Index

The knowledge base is organized into focused Markdown guides:

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

---

## 🛠️ Tooling & Tech Stack

- **Disassemblers & Decompilers**: Ghidra, IDA Pro, Binary Ninja, Radare2 / Cutter.
- **Dynamic Debuggers**: x64dbg, Cheat Engine, ScyllaHide, Process Hacker.
- **AI & Automation**: Antigravity, Claude Code, OpenAI API, Ghidra MCP Server, Python scripts (`pefile`, `capstone`, `keystone`).
- **File Format Analysis**: 010 Editor, ImHex, Kaitai Struct, Hex Fiend.
- **Modern Dev**: C++20, Python 3.12, Qt5/Qt6, OpenGL, Vulkan, CMake.

---

## 🚀 Getting Started

Browse any of the Markdown guides in the [`docs/`](docs/) directory to explore specific topics, or check out our companion projects:
- [project-igi-converter](https://github.com/heaven-hm/project-igi-converter) - Script compiler, decompiler, and multi-format asset conversion engine.
- [project-igi-editor](https://github.com/heaven-hm/project-igi-editor) - 3D level viewport and modding suite.

---

## 📬 Contact & Community

- **Maintainer**: IGI Proz / Heaven-HM
- **Email**: [igiproz.hm@gmail.com](mailto:igiproz.hm@gmail.com)
- **GitHub**: [@heaven-hm](https://github.com/heaven-hm)
- **YouTube**: [IGI Research Devs](https://www.youtube.com/@heaven-hm91)

---

## 📄 License

Distributed under the [MIT License](LICENSE). See `LICENSE` for details.
