# 10. Model Context Protocol (MCP) in Reverse Engineering

## Overview

The **Model Context Protocol (MCP)** provides an open standard for connecting AI assistants (such as Claude Code, Codex, Antigravity, and Cursor) directly to specialized reverse engineering tools and runtime environments.

By exposing disassemblers, decompilers, and debuggers as MCP servers, AI agents can dynamically query binary structures, decompile functions on demand, rename symbols, and verify control flow without manual copy-pasting.

---

## 🏛️ Architecture Overview

```
+-------------------------------------------------------------+
|                      AI Agent Interface                     |
|           (Claude Code / Antigravity / Agentic IDE)         |
+-------------------------------------------------------------+
                              |
                     JSON-RPC / stdio / SSE
                              |
+-----------------------------v-------------------------------+
|                      MCP Server Layer                       |
|   +-------------------+  +-----------------+  +-----------+ |
|   | Ghidra MCP Server |  | IDA Pro MCP     |  | Radare2   | |
|   | (Java / PyGhidra) |  | (IDAPython)     |  | (r2pipe)  | |
|   +-------------------+  +-----------------+  +-----------+ |
+-----------------------------+-------------------------------+
                              |
+-----------------------------v-------------------------------+
|                       Target Binary                         |
|     (Native PE/ELF/Mach-O Executable, Shared Libraries)     |
+-------------------------------------------------------------+
```

---

## 🛠️ Core Capabilities Provided via MCP

| Capability | MCP Tool Name Example | Description |
| :--- | :--- | :--- |
| **Function Listing** | `list_functions` | Enumerates discovered subroutines, names, and address ranges. |
| **On-Demand Decompilation** | `decompile_function` | Decompiles a specific function at an address or symbol name into C pseudocode. |
| **Cross-Reference Mapping** | `get_xrefs_to` / `get_xrefs_from` | Traces callers, callees, and global data references. |
| **Symbol & Variable Renaming** | `rename_function`, `rename_variable` | Updates symbol names in the disassembler database in real time. |
| **Data Type Propagation** | `set_local_variable_type`, `set_prototype` | Synchronizes struct definitions and function prototypes directly into the project. |
| **Disassembly Comments** | `set_decompiler_comment` | Leaves persistent annotations in the reversing database. |
| **String & Asset Scans** | `list_strings`, `list_segments` | Scans for embedded ASCII/UTF-16 strings, sections, and import tables. |

---

## ⚡ Benefits of MCP-Powered Reversing

1. **Elimination of Context Bottlenecks**: Rather than feeding an entire multi-megabyte binary dump to the LLM, the agent queries only relevant functions as needed.
2. **Bidirectional Synchronization**: The agent doesn't just read code—it writes symbols, struct definitions, and comments back into the disassembler database.
3. **Multi-Tool Orchestration**: An agent can combine static decompilation from Ghidra/IDA with fast headless pattern matching from Radare2.

---

## 📚 Related Guides

- [11. Ghidra MCP Setup & Workflows](11_ghidra_mcp_setup_and_workflows.md)
- [12. IDA Pro MCP Setup & Workflows](12_ida_pro_mcp_setup_and_workflows.md)
- [13. Radare2 MCP Workflows](13_radare2_r2pipe_mcp_workflows.md)
- [14. Universal AI Decompilation Prompts](14_universal_ai_decompilation_prompts.md)
