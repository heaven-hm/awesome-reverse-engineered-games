# 11. Ghidra MCP Server: Setup, Integration & Workflows

## Overview

The **Ghidra MCP Server** integrates NSA's Ghidra decompiler with AI assistants over JSON-RPC. It allows agents to explore binary targets interactively, retrieve decompiled C code, query XRefs, define custom data types, and annotate functions autonomously.

---

## 🚀 1. Architecture & Installation

Ghidra MCP bridges your local Ghidra GUI instance or headless analyzer with your AI client (e.g. Claude Code, Antigravity, Cursor).

```
+----------------+      stdio / HTTP      +-----------------------+      Ghidra Bridge      +--------------------+
|   AI Agent     | <====================> |   Ghidra MCP Server   | <=====================> | Ghidra GUI /       |
|  (Claude/Codex)|        JSON-RPC        |    (Python / Node)    |        (TCP / IPC)      | Headless Analyzer  |
+----------------+                        +-----------------------+                         +--------------------+
```

### Installation via `ghidra-bridge` / Python Server:

```bash
# 1. Install ghidra-bridge in your Python environment
pip install ghidra-bridge mcp

# 2. In Ghidra Script Manager:
# Run ghidra_bridge_server.py to open the RPC socket (default port: 48879)
```

### Configuring MCP in `mcp_config.json` / Claude Config:

```json
{
  "mcpServers": {
    "ghidra": {
      "command": "python",
      "args": ["-m", "ghidra_mcp_server", "--port", "48879"],
      "env": {
        "GHIDRA_INSTALL_DIR": "C:/Tools/ghidra_11.0"
      }
    }
  }
}
```

---

## 🛠️ 2. Core Tool Definitions

An effective Ghidra MCP server exposes the following endpoints to the agent:

### `decompile_function`
- **Arguments**: `address` (string) or `function_name` (string).
- **Return**: Full C pseudocode produced by Ghidra's decompiler engine.

### `get_function_xrefs`
- **Arguments**: `address` (string), `direction` (`"to"` | `"from"`).
- **Return**: List of caller/callee function addresses and symbols.

### `set_function_prototype`
- **Arguments**: `address` (string), `prototype` (string, e.g., `void __thiscall Update(Entity* this, float dt)`).
- **Return**: Boolean status confirming type propagation.

### `create_structure` / `set_structure_field`
- **Arguments**: `struct_name` (string), `offset` (integer), `field_name` (string), `field_type` (string).
- **Return**: Confirmation of new struct definition in Ghidra Data Type Manager.

---

## 🔄 3. Typical Agentic Reversing Workflow

```
1. Scan Entrypoints & Strings:
   Agent calls `list_strings(filter="Player")` -> Finds references in `FUN_00412a80`.

2. Decompile Target Subroutine:
   Agent calls `decompile_function(address="0x00412a80")` -> Analyzes game logic.

3. Identify Struct Fields:
   Agent identifies `*(float*)(param_1 + 0x18)` as health and `*(int*)(param_1 + 0x20)` as ammo.

4. Apply Struct & Rename:
   Agent calls `create_structure(name="PlayerEntity")` and sets fields.
   Agent calls `rename_function(address="0x00412a80", new_name="Player_TakeDamage")`.

5. Propagate Changes:
   All other functions referencing `0x00412a80` automatically update in Ghidra.
```

---

## 💡 Best Practices

- **Warmup Headless Analyses**: For large executables (>20MB), run Ghidra Auto-Analysis first before connecting the MCP server to avoid decompiler timeouts.
- **Decompiler Cache**: Cache function decompilations locally during iterative agent loops to reduce latency.
