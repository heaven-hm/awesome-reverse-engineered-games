# 06. AI Prompts & Ghidra Workflows

## Overview

Integrating AI assistants with Ghidra via headless scripts, Python plugins, or Model Context Protocol (MCP) servers accelerates reverse engineering. This guide provides prompt templates and workflow patterns for game reverse engineering.

---

## 1. Reusable AI Prompt Templates

### Prompt 1: Decompiler Refactoring & Type Restoration
```text
Task: Refactor this decompiled C function into modern C++20.
Context: This function is from a 3D DirectX 8 game engine entity system.

Decompiled Input:
[INSERT RAW GHIDRA C CODE]

Requirements:
1. Infer meaningful variable and function names based on context.
2. Identify struct member accesses and define a clear C++ struct layout.
3. Replace magic numbers with typed enums / constants where apparent.
4. Provide a brief explanation of what algorithm or engine subsystem this implements.
```

### Prompt 2: Opcode Dispatcher Extraction
```text
Task: Analyze this switch-case bytecode handler.

Input:
[INSERT SWITCH STATEMENT C CODE]

Requirements:
1. Generate an enum for all opcode values.
2. For each opcode, document the operands read from the instruction stream and stack manipulations.
3. Produce a C++ switch statement or handler function table.
```

### Prompt 3: Binary Struct Layout Deduction
```text
Task: Deduce binary record layout from this parsing loop.

Input:
[INSERT MEMCPY / BUFFER PARSING CODE]

Requirements:
1. Provide a packed C++ struct (`#pragma pack(push, 1)`).
2. Calculate total byte size and alignment.
3. Annotate unknown padding vs meaningful fields.
```

---

## 2. Ghidra Headless Python Scripting

Automate batch decompilation of game binaries to generate context files for AI agents:

```python
# export_decompiled_functions.py (Run via analyzeHeadless)
from ghidra.app.decompiler import DecompInterface
from ghidra.util.task import ConsoleTaskMonitor

monitor = ConsoleTaskMonitor()
decomp = DecompInterface()
decomp.openProgram(currentProgram)

fm = currentProgram.getFunctionManager()
functions = fm.getFunctions(True)

with open("decompiled_output.txt", "w") as f:
    for func in functions:
        res = decomp.decompileFunction(func, 60, monitor)
        if res.decompileCompleted():
            ccode = res.getDecompiledFunction().getC()
            f.write(f"// Function: {func.getName()} @ {func.getEntryPoint()}\n")
            f.write(ccode + "\n\n")
```

---

## 3. Best Practices for AI Reverse Engineering

- **Context Window Management**: Send targeted subroutines along with their immediate callers and callees, rather than dumping entire multi-megabyte disassemblies at once.
- **Cross-Verification**: Never trust an AI-generated struct offset without verifying it against real binary disassemblies or dynamic memory dumps.
- **Document Decisions**: Record discovered structures in central documentation files to build up an iterative knowledge graph.

---

## Next Steps

- Learn about game preservation in [07. Game Engine Preservation](07_game_engine_preservation.md).
