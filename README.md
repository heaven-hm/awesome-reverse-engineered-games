# Awesome Reverse-Engineered Games [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of awesome reverse-engineered, decompiled, and rebuilt games.

Reverse engineering legacy video games combines binary analysis (disassembly, debugging, memory inspection) with modern decompilation and agentic workflows to preserve digital heritage and modernize classic game engines.

## Contents

- [Games](#games)
- [Tools](#tools)
- [Documentation](#documentation)

## Games

| Project | Genre | Tools Used | Methodology & Highlights | Result | Time Taken |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [OpenIGI](https://github.com/OpenIGI/OpenIGI) (2000) | Tactical Stealth FPS | Claude Code + Codex + IDA Pro + Ghidra + Radare2 MCP | Decompiled stripped x86 engine, QVM script VM, MEF meshes, terrain LOD & AI perception via MCP agents. | Complete open-source engine reimplementation (.NET / OpenGL / Vulkan). | 1 month |
| [Legends of Future Past](https://github.com/jonradoff/lofp) (1992) | Multiplayer Online MUD / RPG | Claude Code | Reverse-engineered proprietary scripts, GM manuals & 1996 recordings without source code. | Full Go engine + React + WebSocket + MongoDB rebuild (2,273 rooms, 1,990 items). | One weekend |
| [SkyRoads](https://classicreload.com/skyroads.html) (1993 DOS) | Futuristic 3D Racer / Flyer | Codex | Analyzed raw binary EXE only, disassembled code, built custom software renderer in Rust. | Working native Rust port running on modern OS. | ~6 hours |
| [Disney Infinity 1.0](https://mindstream.news/disney-infinity-ai-mod) (2013) | Commercial Toys-to-Life | Claude Code (Opus) | Traced call graphs in symbol-stripped binary, found 13 character validation checks, generated binary patches. | Universal character unlock mod (unsolved for a decade). | < 24 hours |
| [Chromatron](https://news.ycombinator.com/item?id=43048999) (~2005) | Laser / Mirror Logic Puzzle | Claude Code + Cursor + Ghidra | Decompiled legacy WinXP / PowerPC binaries via GhidrAssistMCP to modern targets. | Native Apple Silicon + WebAssembly ports. | Iterative |
| [Weltendämmerung](https://github.com/adolfintel/weltendaemmerung) (1980s C64) | Turn-based Strategy | Claude Code (Opus 4.5) | Spec-driven reverse engineering from 6502 machine code to modern web stack. | 1:1 accurate web browser port. | 3 days |
| [Tomba!](https://1379.tech) (PS1) | 2.5D Action Platformer | Claude Code + Ghidra + PCSX-Redux | Created a MIPS-to-C++ static recompiler through an iterative agentic feedback loop. | Native Windows port with cutscenes, audio, combat & menus. | ~3 weeks |
| [Era Online](https://era-online-forever.com) (1999) | MMORPG (Visual Basic 6) | Claude Code | Autonomous exploration of client binary and protocol; built extraction tools and modern server. | Full resurrection of the classic 1999 MMORPG. | Short |

- [OpenIGI](https://github.com/OpenIGI/OpenIGI) - Full open-source tactical stealth shooter engine reimplementation of Project I.G.I. in C# and OpenGL.
- [Legends of Future Past](https://github.com/jonradoff/lofp) - Resurrection of the 1992 CompuServe online multiplayer RPG rebuilt in Go, React, and MongoDB.
- [SkyRoads](https://classicreload.com/skyroads.html) - Native Rust port and software rasterizer reverse-engineered from the 1993 MS-DOS space racer binary.
- [Disney Infinity 1.0 Character Unlock](https://mindstream.news/disney-infinity-ai-mod) - Binary patch unlocking all characters across playsets in the commercial action-adventure game.
- [Chromatron](https://news.ycombinator.com/item?id=43048999) - Laser and optics logic puzzle game decompiled and ported to Apple Silicon and WebAssembly.
- [Weltendämmerung](https://github.com/adolfintel/weltendaemmerung) - Commodore 64 fantasy strategy game reverse-engineered into an authentic modern web port.
- [Tomba!](https://1379.tech) - PlayStation 1 platformer static recompiler and native executable port built with disassemblers and emulators.
- [Era Online](https://era-online-forever.com) - 1999 isometric MMORPG reverse-engineered from Visual Basic 6 into C# and Blazor WebAssembly.

## Tools

- [Ghidra](https://ghidra-sre.org) - Software reverse engineering framework developed by the NSA.
- [IDA Pro](https://hex-rays.com/ida-pro) - Multi-processor disassembler and Hex-Rays decompiler.
- [Radare2](https://rada.re/n/radare2.html) - Open-source binary analysis framework, disassembler, and command-line hex editor.
- [x64dbg](https://x64dbg.com) - Open-source x64/x32 debugger for Windows.
- [Cheat Engine](https://www.cheatengine.org) - Open-source development environment focused on memory scanning, debugging, and runtime modification.
- [PCSX-Redux](https://github.com/grumpycoders/pcsx-redux) - PlayStation 1 emulator with debugging, scripting, and OpenBIOS support.
- [Kaitai Struct](https://kaitai.io) - Declarative binary format parsing and struct specification language.
- [ImHex](https://imhex.werwolv.net) - Hex editor designed for reverse engineers, programmers, and binary researchers.
- [Claude Code](https://github.com/anthropics/claude-code) - Agentic command-line AI coding assistant by Anthropic.

## Documentation

- [AI Reverse Engineering Guide](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/01_introduction.md) - Introduction to reverse engineering workflows assisted by large language models.
- [Static Analysis and Decompilation](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/02_static_analysis_and_decompilation.md) - Workflows for decompilation, symbol recovery, and type restoration.
- [Dynamic Analysis and Memory](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/03_dynamic_analysis_and_memory.md) - Techniques for runtime memory scanning, pointer tracing, and function hooking.
- [File Format Reconstruction](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/04_file_format_reconstruction.md) - Methodology for decoding proprietary 3D meshes, textures, and archive containers.
- [Bytecode and Scripting Engines](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/05_bytecode_and_scripting_engines.md) - Analysis of custom virtual machines, opcode dispatchers, and bytecode compilation.
- [Ghidra and AI Workflows](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/06_ai_prompts_and_ghidra_workflows.md) - Automation scripts and reusable prompt templates for binary analysis.
- [Game Engine Preservation](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/07_game_engine_preservation.md) - Architectural patterns for building modern source ports and level editors.
- [Project I.G.I. Case Study](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/08_case_studies_project_igi.md) - Technical deep-dive into legacy game engine reversing and asset conversion.
- [Documented Rebuild Projects](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/09_documented_ai_reverse_engineering_projects.md) - Comprehensive catalog of game rebuild and decompilation case studies.
- [MCP Architecture](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/10_mcp_reverse_engineering_architecture.md) - Overview of Model Context Protocol integration with binary analysis environments.
- [Ghidra MCP Server](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/11_ghidra_mcp_setup_and_workflows.md) - Setup guide for connecting language models directly to the Ghidra decompiler.
- [IDA Pro MCP Server](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/12_ida_pro_mcp_setup_and_workflows.md) - IDAPython server configuration for Hex-Rays decompiler tool calling.
- [Radare2 MCP Workflows](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/13_radare2_r2pipe_mcp_workflows.md) - Headless binary analysis, control flow extraction, and emulation via r2pipe.
- [Universal Decompilation Prompts](https://github.com/heaven-hm/awesome-reverse-engineered-games/blob/main/docs/14_universal_ai_decompilation_prompts.md) - Reusable prompt templates for 3D mathematics, physics, and entity loops.
