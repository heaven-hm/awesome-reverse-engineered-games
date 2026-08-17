# 03. Dynamic Analysis & Memory Forensics

## Overview

Dynamic analysis validates static hypotheses by observing game execution at runtime. By attaching debuggers (x64dbg, Cheat Engine) and hooking key subroutines, we can intercept live entity pointers, track state transitions, and dump decrypted assets directly from memory.

---

## 1. Memory Scanning & Pointer Path Finding

### Finding Core Game Pointers
1. **Value Scanning**:
   - Search for player attributes: Health (float / int32), Ammo (int32), Coordinates (3x float), Camera Angles (Yaw/Pitch float).
2. **Access Breakpoints ("Find out what writes/accesses this address")**:
   - Set a hardware breakpoint on the target memory address.
   - Trigger the action in-game (e.g. fire weapon, take damage).
   - Capture the instruction address, register states (`EAX`, `ECX`, `ESI`, `EDI`), and instruction displacement.
3. **Pointer Multilevel Chains**:
   - Trace backwards from `LocalPlayerPtr` to `EntityList` to `GameWorldSingleton`.
   - Pattern: `[[[[BaseModule.exe + 0x2A1940] + 0x48] + 0x10] + 0x24] = PlayerHealth`.

---

## 2. API Hooking & Runtime Interception

### DirectX / OpenGL Hooking
Hooking the graphics swap chain / render loop (`Present`, `EndScene`, or `wglSwapBuffers`) provides a consistent frame-based hook for custom overlays, telemetry, and entity dumps:

```cpp
// Example: Direct3D 9 EndScene Hook Pattern
typedef HRESULT (APIENTRY *tEndScene)(LPDIRECT3DDEVICE9 pDevice);
tEndScene oEndScene = nullptr;

HRESULT APIENTRY hkEndScene(LPDIRECT3DDEVICE9 pDevice) {
    // 1. Inspect game world state
    GameWorld* world = GetGameWorld();
    if (world && world->player) {
        // Log player position or draw debug gizmos
    }
    
    // 2. Call original function
    return oEndScene(pDevice);
}
```

### Detour Hooking Subroutines
Using MinHook, Microsoft Detours, or custom inline trampolines to intercept file I/O or script execution:
- Hook `fopen`, `CreateFileA`, `ReadFile` to observe asset loading order and uncompressed buffer sizes.
- Hook script VM execution routines to log bytecode instructions in real time.

---

## 3. Signature Scanning (Pattern Matching)

To make tools resilient to minor patch updates or different language builds:
```cpp
// Pattern: 55 8B EC 83 EC ?? 53 56 8B 75 08
uintptr_t FindPattern(const char* moduleName, const char* pattern, const char* mask) {
    MODULEINFO modInfo = GetModuleInfo(moduleName);
    uint8_t* base = (uint8_t*)modInfo.lpBaseOfDll;
    size_t size = modInfo.SizeOfImage;
    size_t patternLen = strlen(mask);

    for (size_t i = 0; i < size - patternLen; ++i) {
        bool found = true;
        for (size_t j = 0; j < patternLen; ++j) {
            if (mask[j] != '?' && pattern[j] != *(char*)(base + i + j)) {
                found = false;
                break;
            }
        }
        if (found) return (uintptr_t)(base + i);
    }
    return 0;
}
```

---

## Next Steps

- Move to [04. Binary File Format Reconstruction](04_file_format_reconstruction.md) to learn how to unpack and decode proprietary archives.
