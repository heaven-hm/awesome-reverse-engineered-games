# 05. Bytecode & Scripting Engines

## Overview

Many vintage and modern game engines execute mission logic, AI state machines, dialogue trees, and cutscenes inside an internal Virtual Machine (VM) running custom bytecode (e.g. QuakeC, UnrealScript, SCUMM, Project I.G.I. QVM/QSC).

Reconstructing these virtual machines enables:
1. Decompiling compiled mission scripts back into human-readable high-level source code.
2. Writing custom mission compilers to create entirely new game campaigns.
3. Modifying AI behaviors and mission triggers without modifying the executable.

---

## 1. Locating the Opcode Dispatcher

In the disassembler, search for the main interpreter loop. It typically exhibits one of two architectures:

### Pattern A: Switch-Based Dispatcher
```cpp
void ExecuteVM(VMContext* ctx) {
    while (ctx->running) {
        uint8_t opcode = *ctx->pc++;
        switch (opcode) {
            case OP_NOP:
                break;
            case OP_PUSH_CONST:
                PushStack(ctx, ReadInt32(ctx));
                break;
            case OP_ADD: {
                int32_t b = PopStack(ctx);
                int32_t a = PopStack(ctx);
                PushStack(ctx, a + b);
                break;
            }
            case OP_CALL_NATIVE: {
                uint16_t funcId = ReadUInt16(ctx);
                CallNativeFunction(ctx, funcId);
                break;
            }
            // ...
        }
    }
}
```

### Pattern B: Direct Jump Table / Computed GOTO
```c
// Assembly pattern in x86:
// MOVZX EAX, BYTE PTR [ESI]      ; Load opcode
// INC ESI                        ; Increment Program Counter
// JMP DWORD PTR [EAX*4 + 0x48A000] ; Jump to handler function
```

---

## 2. Categorizing VM Instruction Sets

1. **Stack-Based vs. Register-Based**:
   - Stack-based machines push operands onto an evaluation stack (`OP_PUSH`, `OP_POP`, `OP_ADD`).
   - Register-based machines specify source and destination virtual registers (`OP_ADD R0, R1, R2`).
2. **Control Flow**:
   - `OP_JMP` (unconditional jump relative/absolute).
   - `OP_JZ` / `OP_JNZ` (conditional jump based on top-of-stack or flag register).
   - `OP_CALL` / `OP_RET` (subroutine invocation with frame setup).
3. **Engine Native Interop (Syscalls)**:
   - Instructions invoking native engine functions (e.g., `PlaySound`, `SpawnActor`, `SetObjectiveState`, `CheckPlayerDistance`).

---

## 3. Building an AST and Decompiler Pipeline

```
  +---------------+       +---------------+       +---------------+       +---------------+
  | Bytecode File | ----> | Disassembler  | ----> | Control Flow  | ----> | High-Level    |
  | (.QVM / .BIN) |       | (Raw Opcodes) |       | Graph & AST   |       | Source (.QSC) |
  +---------------+       +---------------+       +---------------+       +---------------+
```

1. **Disassembly Stage**: Convert raw binary bytes into sequential instruction tokens.
2. **Control Flow Analysis**: Identify basic blocks, branch targets, loops (`while`, `for`), and conditions (`if/else`).
3. **Expression Tree Reconstruction**: Collapse stack operations into high-level mathematical and relational expressions (e.g., `Push A, Push B, Add` becomes `A + B`).
4. **Code Generation**: Emit clean, human-readable script text.

---

## Next Steps

- Check out [06. AI Prompts & Ghidra Workflows](06_ai_prompts_and_ghidra_workflows.md) for prompt templates to automate opcode mapping.
- Review [08. Case Studies: Project I.G.I.](08_case_studies_project_igi.md) for real-world QVM/QSC tooling.
