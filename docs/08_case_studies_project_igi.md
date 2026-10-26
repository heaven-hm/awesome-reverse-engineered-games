# 08. Case Studies: Project I.G.I. (I'm Going In)

## Overview

*Project I.G.I.: I'm Going In* (Innerloop Studios, 2000) is a milestone tactical stealth first-person shooter powered by Innerloop's proprietary Joint Strike Fighter (JSF) flight-simulator engine. 

This case study highlights how reverse engineering methods were applied to decipher I.G.I.'s proprietary scripting virtual machine, level formats, and 3D geometry.

---

## 1. The QVM / QSC Scripting System

I.G.I. levels are governed by script packages known as `QVM` (compiled bytecode) and human-authored `QSC` (source scripts):

- **Script Hierarchy**: Scripts define task graphs, guard patrol routes, alarm states, camera triggers, and mission objectives.
- **Task Trees**: Objectives are expressed as hierarchical tasks (`c_task`, `c_sequence`, `c_parallel`, `c_guard_task`).
- **AI Behavior Dispatch**: AI perception systems (sound detection radius, visual sight cones, alertness levels) are driven by script variables and native callbacks.

### Decompiler / Compiler Implementation: `project-igi-converter`
- **Compiler**: Parses high-level `.qsc` syntax, builds an AST, calculates stack offsets, resolves symbols, and outputs binary `.qvm` bytecode.
- **Decompiler**: Disassembles binary `.qvm` instructions, recovers control flow structures, and reproduces clean `.qsc` source files.

---

## 2. 3D Mesh and Level Formats (.MEF / .LEV / .TEX)

1. **3D Models (.MEF)**:
   - Contains vertex streams, normals, texture UV coordinates, level-of-detail (LOD) tables, and collision primitives (boxes, cylinders, convex hulls).
   - Reconstructed into modern Blender import/export plugins and Qt 3D viewports.
2. **Textures (.TEX / .PIC)**:
   - Paletted 8-bit, 16-bit 565/5551 RGB formats, and compressed texture blocks.
   - Decoded into standard 32-bit RGBA PNG / DDS textures.
3. **Terrain and Heightmaps**:
   - Continuous level terrain rendered with dynamic LOD algorithms derived from the JSF flight engine.

---

## 3. Reverse Engineering & Tooling Ecosystem

The reverse engineering community for Project I.G.I. and I.G.I.-2 has produced active decompilations, recompilations, and modding tools:

### Recompilation, Decompilation & Source Ports
- **[IGI Recomp](https://github.com/HenryKun55/igi-recomp)** (by [@HenryKun55](https://github.com/HenryKun55)): Ahead-of-Time (AOT) static binary recompilation of retail `IGI.exe` to portable C running on macOS (Apple Silicon ARM64), PS Vita, and PC at 60+ FPS with modern OpenGL rendering and FFmpeg Indeo 5 video playback.
- **[IGI-RE](https://github.com/slickdaddyy/IGI-RE)** (by [@slickdaddyy](https://github.com/slickdaddyy)): Function recovery, disassembled game logic analysis, and decompilation targeting the original Project I.G.I. binary.
- **[Project Open IGI](https://github.com/heaven-hm/project-open-igi)** (by [@heaven-hm](https://github.com/heaven-hm)): Modern C++20 engine reconstruction and source port with strict CFG concordance gates, DirectDraw/Direct3D 7 rendering, and QVM virtual machine integration.
- **[OpenIGI](https://github.com/OpenIGI/OpenIGI)** (by [@ShahriyarB](https://github.com/ShahriyarB)): Clean-room multi-game engine reimplementation in C# on .NET 10 supporting both *Project I.G.I.* and *I.G.I. 2: Covert Strike*.
- **[IGI 2 Decomp](https://github.com/ShahriyarB/igi2-decomp)** (by [@ShahriyarB](https://github.com/ShahriyarB)): Reverse engineering and decompilation project targeting *I.G.I.-2: Covert Strike*.
- **[project-igi-reverse-engineering](https://github.com/heaven-hm/project-igi-reverse-engineering)**: Curated index and central directory of all reverse-engineering and source-port efforts across the I.G.I. series.

### Asset Converters & Editor Tools
- **[project-igi-editor](https://github.com/heaven-hm/project-igi-editor)**: Modern 3D level navigation and modding editor.
- **[project-igi-converter](https://github.com/heaven-hm/project-igi-converter)**: C++ Qt multi-format asset conversion engine and QSC/QVM compiler/decompiler.
- **[project-igi-qvm-editor](https://github.com/heaven-hm/project-igi-qvm-editor)**: Legacy script manipulation toolkit.

---

## 4. Key Learnings & Takeaways

- **Systematic Structure Logging**: Keeping rigorous documentation of every byte offset and data type accelerates tooling development across multiple tools.
- **AI-Assisted Decoding**: Modern LLMs can instantly recognize standard trigonometric and linear algebra algorithms inside raw disassembly, saving days of manual graph tracing.
- **Community Preservation**: Reverse engineering legacy games preserves digital heritage and enables new generations of modders to build upon classic foundations.
