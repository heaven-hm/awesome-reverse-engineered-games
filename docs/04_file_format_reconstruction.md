# 04. Binary File Format Reconstruction

## Overview

Game engines store graphics, audio, levels, and animations in custom binary formats. Reverse engineering these formats allows community modding, asset extraction, modern re-rendering, and format converters.

---

## 1. Systematic Format Dissection

When examining an unknown file format in a hex editor (e.g. 010 Editor, ImHex):

### Step 1: Identify the Header
- **Magic Number**: Look at the first 4 to 8 bytes (e.g. `RIFF`, `PACK`, `FORM`, `MEF_`, `QVM\0`).
- **Version Number**: Usually follows magic bytes (`uint32_t` or `uint16_t`, e.g. `0x00000001`).
- **TOC (Table of Contents) Offset**: Pointer or file offset to where records / chunk descriptors begin.
- **Record Count**: Total number of entries or meshes contained in the file.

### Step 2: Identify Chunking / Tree Structures
Many game engines use IFF-style or RIFF-style hierarchical chunks:
```
[Chunk FourCC (4 bytes)] [Chunk Size (4 bytes)] [Payload (N bytes)]
```

### Step 3: Differentiate Data Types
- **Integers**: Indices, face counts, vertex counts, flags (int16 / int32, little-endian).
- **Floating Points**: Coordinates, normals, UVs, bounding spheres (IEEE 754 float32, range usually between -10000.0 and +10000.0).
- **Strings**: Null-terminated ASCII, Pascal strings (length prefix + chars), or fixed-length 32/64 byte buffers.

---

## 2. 3D Model & Mesh Structure Patterns

Standard vertex buffers in classic game engines follow predictable interleaved formats:

```cpp
#pragma pack(push, 1)

struct VertexP3F_N3F_T2F {
    float x, y, z;       // Position (12 bytes)
    float nx, ny, nz;    // Normal (12 bytes)
    float u, v;          // Texture coordinates UV (8 bytes)
};                       // Total: 32 bytes per vertex

struct MeshFaceIndex {
    uint16_t v0;
    uint16_t v1;
    uint16_t v2;
};

struct MeshHeader {
    char magic[4];       // e.g. "MESH"
    uint32_t vertexCount;
    uint32_t faceCount;
    uint32_t materialId;
    float boundingBoxMin[3];
    float boundingBoxMax[3];
};

#pragma pack(pop)
```

---

## 3. Reverse Engineering Archive Containers (.RES, .PAK, .DAT)

Common archive format layout:
```
+-------------------------------------------------------+
| Header: Magic | Version | EntryCount | TOC_Offset     |
+-------------------------------------------------------+
| Data Payloads: (Raw / LZSS / Zlib / LZO Compressed)   |
|   ... Compressed File 1 ...                           |
|   ... Compressed File 2 ...                           |
+-------------------------------------------------------+
| Table of Contents (TOC):                              |
|   Entry 1: [FileName / Hash] [Offset] [CompSz] [RawSz]|
|   Entry 2: [FileName / Hash] [Offset] [CompSz] [RawSz]|
+-------------------------------------------------------+
```

### LLM Prompt Strategy for File Formats
Provide a hex dump (first 256 bytes + TOC slice) and ask the AI agent:
> *"Here is the hex header of an uncompressed game asset. Note the count of 14 at offset 0x08 and repeating 16-byte records starting at 0x10. Calculate record boundaries and generate a Kaitai Struct specification or C++ deserializer."*

---

## Next Steps

- Explore script bytecode reversing in [05. Bytecode & Scripting Engines](05_bytecode_and_scripting_engines.md).
