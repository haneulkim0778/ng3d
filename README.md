# ng3d

> **Status:** Early Bootstrap (Phase 0) — Establishing architecture decision records, C++23 safety tooling, and CI foundations.

**ng3d** is a C++23 and modern Vulkan (1.3+) real-time 3D engine focused on pushing visual quality and frame-time stability on **constrained, unified-memory hardware** (integrated laptop GPUs and handhelds) without requiring hardware ray tracing or tensor acceleration.

## Design Philosophy

1. **Evidence-First Architecture (MADR)**
   Major technical choices are documented as [Markdown Architectural Decision Records](docs/adr/) backed by peer-reviewed computer graphics literature, Khronos specifications, and reproducible GPU benchmarks.
2. **Constrained-Hardware Baseline**
   Designed from day one for bandwidth-limited, shared-memory integrated GPUs:
   - **Render Graph** scheduling for explicit resource lifetimes and memory aliasing (*FrameGraph*, O'Donnell, GDC 2017)
   - **GPU-Driven Culling** to minimize CPU draw-call overhead (*GPU-Driven Rendering Pipelines*, Haar & Aaltonen, SIGGRAPH 2015)
   - **Visibility Buffer** deferred shading to minimize G-buffer bandwidth (*The Visibility Buffer*, Burns & Hunt, JCGT 2013)
   - **Hardware-RT-Free Global Illumination** research direction (*Radiance Cascades*, Sannikov, 2023)
3. **Strict C++23 Safety & Hygiene**
   Adopts Rust-inspired engineering discipline in modern C++23 (`std::expected`, RAII ownership, `std::span`, strong handle types, `/W4 /WX`, `clang-tidy` with `cppcoreguidelines-*`, ASan/UBSan).
4. **Agent-Friendly & Verifiable**
   Text-first declarative structures, headless Vulkan validation and snapshot testing, and deterministic GPU timestamp telemetry.

## Roadmap

- **Phase 0:** Repository standards, CI pipeline, `clang-format`/`clang-tidy`, `CMakePresets`, `vcpkg` manifest, and foundational ADRs (`0000`–`0003`)
- **Phase 1:** Modern Vulkan RHI (`Dynamic Rendering`, `Synchronization2`, Timeline Semaphores, VMA) + headless snapshot & validation harness
- **Phase 2:** FrameGraph + standard `glTF 2.0` / `meshoptimizer` asset ingestion
- **Phase 3:** GPU-Driven culling + Visibility Buffer material pass
- **Phase 4:** Dynamic lighting, RT-free GI, VRS, and crisp temporal reconstruction

## License

Licensed under the [MIT License](LICENSE).
