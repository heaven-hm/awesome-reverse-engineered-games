# 02. Static Analysis & Decompilation with LLMs

## Overview

Static analysis involves analyzing the target binary without executing it. In game binaries (x86, x86-64, ARM, MIPS), compilers strip symbol names, optimize away structs, inline functions, and generate complex control flow graphs.

This guide covers how to systematically recover clean C++ structures and functions using decompilers assisted by AI.

---

## 1. Ghidra & IDA Setup Best Practices

1. **Base Address & Relocations**: Always verify the executable base address. For older DirectX 7/8/9 titles, executables are typically fixed at `0x00400000`.
2. **Standard Library & Compiler Signature Matching**:
   - Apply FLIRT signatures (IDA) or Function ID databases (Ghidra) for MSVC runtime versions (e.g. MSVC 6.0, MSVC 2003, MSVC 2008, GCC).
   - This eliminates standard library functions (`malloc`, `memcpy`, `operator new`, `printf`) from your analysis scope.
3. **String Table & RTTI Analysis**:
   - Run string analysis scripts. In game engines, debug assertion strings (e.g. `Assertion failed in 'c_game_entity.cpp' line 342`) provide immediate clues regarding class names and member roles.
   - Scan for RTTI (Run-Time Type Information) descriptors to reconstruct C++ class hierarchies and vtables.

---

## 2. Struct Recovery Workflow

When a function dereferences multiple offsets from a single base pointer (`ECX` / `this`), it indicates a struct or class instance:

### Raw Decompiled Output
```c
void FUN_00451a20(int *this, float param_1, float param_2, float param_3) {
    *(float *)(this + 4) = *(float *)(this + 4) + param_1;
    *(float *)(this + 5) = *(float *)(this + 5) + param_2;
    *(float *)(this + 6) = *(float *)(this + 6) + param_3;
    *(int *)(this + 10) |= 1;
}
```

### AI-Assisted Struct Deduction Prompt
> *"Analyze the following decompiler snippet. Notice the 3 consecutive float additions and a bitwise flag update at offset 40 (0x28). Deduce the likely struct layout and member names."*

### Reconstructed C++ Structure
```cpp
struct Vector3 {
    float x;
    float y;
    float z;
};

struct GameEntity {
    void* vtable;            // 0x00
    Vector3 position;        // 0x04, 0x08, 0x0C
    Vector3 rotation;        // 0x10, 0x14, 0x18
    Vector3 velocity;        // 0x1C, 0x20, 0x24
    uint32_t flags;          // 0x28: Bit 0 = DIRTY_TRANSFORM
};

void GameEntity::Translate(const Vector3& delta) {
    this->position.x += delta.x;
    this->position.y += delta.y;
    this->position.z += delta.z;
    this->flags |= ENTITY_FLAG_DIRTY;
}
```

---

## 3. VTable & Virtual Function Mapping

Virtual method tables are arrays of function pointers located at offset `0x00` of a C++ object:
1. Locate the constructor function where the object's vtable pointer (`vptr`) is initialized:
   ```c
   *(int *)this = 0x004a8b20; // Address of vtable
   ```
2. Inspect `0x004a8b20` in the data segment:
   - Index 0: `FUN_00452100` -> `virtual ~GameEntity()`
   - Index 1: `FUN_00452180` -> `virtual void Update(float dt)`
   - Index 2: `FUN_00452240` -> `virtual void Render(RenderContext* ctx)`
   - Index 3: `FUN_00452310` -> `virtual void OnCollision(Entity* other)`
3. Create a Ghidra / IDA vtable struct to automatically populate method signatures across all callsites.

---

## Next Steps

- Explore runtime memory debugging in [03. Dynamic Analysis & Memory Forensics](03_dynamic_analysis_and_memory.md).
