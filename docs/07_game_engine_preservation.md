# 07. Game Engine Preservation & Modernization

## Overview

Classic game engines developed in the 1990s and 2000s face obsolescence due to modern operating system changes, deprecation of legacy graphics APIs (DirectDraw, Direct3D 5/6/7/8), multi-monitor scaling issues, and modern high-DPI displays.

Engine preservation aims to rebuild and modernize these engines so they can be played, modded, and studied on modern hardware.

---

## 1. Architectural Layers of Modern Source Ports

```
+-------------------------------------------------------------+
|                     High-Level Game Logic                   |
|           (Player Controller, AI States, Inventory, Level)   |
+-------------------------------------------------------------+
|                     Engine Abstraction Layer                |
|       +-----------------+-----------------+-----------------+
|       |  Render Backend |  Audio Backend  |  Input / Window |
|       +-----------------+-----------------+-----------------+
|       | OpenGL 3.3/4.5  | OpenAL / Mini-  | SDL2 / GLFW3    |
|       | Vulkan / D3D11  | audio / SoLoud  |                 |
+-------+-----------------+-----------------+-----------------+
|                     Platform OS Layer (Win/Linux/Mac)       |
+-------------------------------------------------------------+
```

---

## 2. Replacing Fixed-Function Pipelines with Modern Shaders

Early Direct3D titles relied on the fixed-function pipeline (`SetTransform(D3DTS_WORLD, ...)`, `SetLight`, `SetTextureStageState`). In modern rendering pipelines:

1. **Matrix Management**:
   - Replace legacy hardware matrix stacks with modern GLM / Eigen transform matrices:
     ```cpp
     glm::mat4 modelMatrix = glm::translate(glm::mat4(1.0f), entity.position) * glm::toMat4(entity.rotation);
     glm::mat4 mvp = projectionMatrix * viewMatrix * modelMatrix;
     ```
2. **Standard Vertex & Fragment Shaders**:
   - Write GLSL / HLSL shaders that replicate classic gouraud shading, directional lighting, fog effects, and multi-texturing.

---

## 3. Modern Tooling & 3D Level Editors

Preservation extends beyond just running the game—it requires creating modern toolchains for content creation:
- **3D Viewport Editors**: Built using frameworks like Qt (with QOpenGLWidget) or Dear ImGui.
- **Gizmo Transform Tools**: Interactive translation, rotation, and scale manipulators for placing game objects in 3D space.
- **Live Asset Reloading**: Hot-reloading scripts, textures, and geometry without restarting the game.

---

## Next Steps

- Review real-world examples in [08. Case Studies: Project I.G.I.](08_case_studies_project_igi.md).
