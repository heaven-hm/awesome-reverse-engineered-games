# 01. Introduction to AI-Assisted Game Reverse Engineering

## Overview

Reverse engineering video games entails recovering high-level architectural knowledge, algorithms, data structures, and file formats from compiled machine code and raw binary data. 

Traditionally, this process required thousands of hours of manual labor in disassemblers and hex editors. With the integration of Large Language Models (LLMs) and agentic frameworks, reverse engineers can automate boilerplate analysis, decode unknown bytecode, annotate cryptic decompiler outputs, and generate clean C++ source implementations rapidly.

---

## The AI Reverse Engineering Loop

```
  +------------------+         +------------------+         +------------------+
  |  Binary Target   | ------> |  Ghidra / IDA    | ------> | Decompiled Code  |
  |  (EXE, DLL, DAT) |         |  Disassembler    |         | (Raw C / ASM)    |
  +------------------+         +------------------+         +------------------+
                                                                     |
                                                                     v
  +------------------+         +------------------+         +------------------+
  | Verified Source  | <------ | Agent Validation | <------ | LLM Reasoning    |
  | (C++ Engine Mod) |         | & Type Checking  |         | & Reconstruction |
  +------------------+         +------------------+         +------------------+
```

### 1. Extraction & Context Generation
- Decompile targeted subroutines using tools like Ghidra, IDA Pro, or Binary Ninja.
- Collect cross-references (XRefs), string literals, import tables, and data segment references.
- Structure this information into contextual prompts for the AI agent.

### 2. Semantic Analysis & Hypothesis Generation
- The LLM identifies standard patterns (e.g. vector math, matrix multiplications, bounding box collision checks, audio mixers, Huffman decoding, network packet handlers).
- Unknown struct layouts and member offsets (`param_1 + 0x1c`) are deduced and mapped to intuitive C++ fields.

### 3. Structuring and Verification
- The deduced structs, function signatures, and reconstructed algorithms are cross-referenced with dynamic debugging observations (Cheat Engine / x64dbg).
- Unit tests and standalone test harness scripts verify the accuracy of the reconstructed logic.

---

## Key Domains of Application

1. **Static Analysis & Decompilation**: Transforming obfuscated assembly or decompiler output into clean, idiomatic C++ with meaningful variable and function names.
2. **Binary Asset & Archive Formats**: Deciphering proprietary mesh formats, texture encodings, audio containers, and scene descriptors.
3. **Scripting Virtual Machines**: Reconstructing bytecode instruction sets, opcode dispatchers, and generating script compilers/decompilers.
4. **Memory Forensics & Modding**: Identifying game object hierarchies, entity managers, physics states, and creating runtime hooks or plugins.
5. **Engine Source Porting**: Building modernized, portable cross-platform source ports for retro game engines.

---

## Next Steps

- Proceed to [02. Static Analysis & Decompilation](02_static_analysis_and_decompilation.md) to explore static decompilation techniques.
- Review [06. AI Prompts & Ghidra Workflows](06_ai_prompts_and_ghidra_workflows.md) for ready-to-use prompt templates.
