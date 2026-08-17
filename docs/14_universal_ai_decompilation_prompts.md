# 14. Universal AI Decompilation Prompts & Patterns

## Overview

A collection of generic, battle-tested prompt templates and agent strategies for decompiling and reconstructing game engine subsystems from raw assembly or decompiler pseudocode. These patterns apply universally to any 3D/2D game engine (DirectX, OpenGL, Vulkan, Unreal, Unity native, custom retro engines).

---

## 🎯 1. 3D Math & Transform Pipelines

```text
Task: Refactor decompiled matrix and vector mathematics.
Input Pseudocode:
[INSERT RAW DECOMPILER CODE]

Instructions:
1. Identify all 3D operations (e.g. Dot Product, Cross Product, Matrix Inversion, Quaternions, Euler angles, Projection transforms).
2. Replace pointer arithmetic (e.g., *(float*)(ptr + 12)) with glm::vec3, glm::vec4, or glm::mat4 syntax.
3. Emit clean, const-correct modern C++ functions.
```

---

## 🎯 2. Collision Detection & Bounding Volumes

```text
Task: Reconstruct collision detection logic from this binary subroutine.
Input Pseudocode:
[INSERT RAW DECOMPILER CODE]

Instructions:
1. Identify bounding volume types used (AABB, OBB, Bounding Sphere, Capsule, Raycast, Convex Hull).
2. Deduce the return value meaning (boolean intersection vs. hit result with penetration depth & normal vector).
3. Produce a structured RaycastHit or CollisionResult struct in C++.
```

---

## 🎯 3. Entity Component Systems & Game State Loops

```text
Task: Reverse engineer this entity update loop.
Input Pseudocode:
[INSERT RAW DECOMPILER CODE]

Instructions:
1. Identify the container type (dynamic array, linked list, sparse set, hash map).
2. Trace the virtual function dispatch (`*(code**)(*this + offset)`).
3. Identify member variables updated per tick (e.g., position += velocity * deltaTime; health depletion; lifetime counter).
4. Reconstruct clean C++ entity classes and an EntityManager / WorldScene update loop.
```

---

## 🎯 4. Bytecode Virtual Machine & Opcode Handler

```text
Task: Reconstruct an opcode instruction set and execution stack.
Input Pseudocode:
[INSERT SWITCH / JUMP TABLE DECOMPILATION]

Instructions:
1. Create a strongly-typed enum for all discovered opcodes.
2. For each opcode, document:
   - Operands consumed from instruction stream (immediate values, registers, string IDs).
   - Evaluation stack pushes and pops.
   - Native engine callbacks / syscalls triggered.
3. Produce a clean C++ virtual machine dispatcher loop with error handling.
```

---

## 🎯 5. Binary File Format & Archive Parser

```text
Task: Construct a C++ parser and Kaitai Struct specification for this unknown file format.
Context: File begins with header chunk parsing loop.
Input:
[INSERT HEX DUMP + DECOMPILED PARSING FUNCTION]

Instructions:
1. Identify the file header (Magic bytes, format version, table of contents offset, chunk count).
2. Map all record offsets and structure field sizes (uint8, uint16, uint32, float, null-terminated strings).
3. Write a packed C++ structure definition (`#pragma pack(push, 1)`) and a deserializer function with endianness safety.
```
