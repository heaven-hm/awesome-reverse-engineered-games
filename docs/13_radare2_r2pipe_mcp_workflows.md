# 13. Radare2 & r2pipe MCP Workflows

## Overview

**Radare2 (r2)** is a lightweight, Unix-first, highly extensible binary analysis framework. When paired with **`r2pipe`** and MCP, Radare2 gives AI agents ultra-fast, headless access to disassembly, Control Flow Graphs (CFGs), binary diffing, and ESIL (Evaluable String Intermediate Language) emulation.

---

## 🚀 1. Architecture & Setup

Radare2 is uniquely suited for autonomous AI agent pipelines because it requires no heavy GUI or JVM runtime, and boots in milliseconds.

```
+--------------------+      stdio JSON-RPC      +----------------------+      Native IPC      +--------------------+
|      AI Agent      | <======================> |   Radare2 MCP Server | <==================> |   r2 core process  |
|  (Claude / Codex)  |                          |     (Python FastMCP) |      (r2pipe)        |   (libr_core)      |
+--------------------+                          +----------------------+                      +--------------------+
```

### Quick Installation:

```bash
# 1. Install Radare2 and r2pipe
pip install r2pipe mcp

# 2. Start MCP server pointing to binary
python -m radare2_mcp_server --binary game_executable.exe
```

---

## 🛠️ 2. Key Radare2 Commands Exposed via MCP

Radare2's JSON output flags (`j` suffix) make it natively designed for programmatic consumption:

| MCP Tool | Underlying r2 Command | Description |
| :--- | :--- | :--- |
| `r2_analyze` | `aaa` / `aac` | Performs deep auto-analysis, function discovery, and call tree parsing. |
| `r2_list_functions` | `aflj` | Returns JSON array of all functions with sizes, offsets, and basic block counts. |
| `r2_disassemble_function` | `pdfj @ <addr>` | Returns JSON representation of disassembled instructions and branch targets. |
| `r2_decompile` | `pdgj @ <addr>` / `pddj` | Decompiles function using Ghidra plugin (`r2ghidra`) or R2Dec. |
| `r2_get_cfg` | `agj @ <addr>` | Extracts the full Control Flow Graph (basic blocks, jump conditions). |
| `r2_emulate_step` | `aei`, `aes` | Emulates ESIL instructions to evaluate register outcomes without executing native code. |
| `r2_binary_diff` | `radiff2 -j binA binB` | Generates graph and byte-level diffs between binary versions/patches. |

---

## ⚡ 3. Advanced Use Cases

### 1. ESIL Emulation for Crypto & Unpacking Routines
Instead of guessing how a custom decryption loop or hashing algorithm works, an AI agent can execute `r2` ESIL emulation:
```bash
# Initialize ESIL VM, set registers, step 10 instructions, and inspect output
aei; aeim; ar eax=0x1234; 10aes; arj
```

### 2. Fast Binary Diffing Across Game Patches
When a new game patch drops, the AI agent invokes `radiff2` via MCP to find modified functions and explain the exact gameplay or security changes made in the update.

---

## 💡 Best Practices

- Always initialize with `aaa` for full analysis or `aac` for basic block reference parsing.
- Use `r2ghidra` extension (`r2pm -ci r2ghidra`) inside Radare2 to combine r2's speed with Ghidra's decompiler backend.
