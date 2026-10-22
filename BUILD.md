# Build dependencies

## Required
- C++20 minimum, C++26 preferred
  - CMake ≥ 3.20
  - Compiler: GCC ≥ 12 / Clang ≥ 15 (C++20); newer for C++26
  - Threads (pthread) — used by the parallel batch queue
- Toplethos: submodule at `toplethos_lang/`
  ```bash
  git submodule update --init toplethos_lang
  ```
  Post-parallelism update (Halloween 2026 or later).

## Optional
- Lean 4 (specs only): `elan toolchain install stable`
  - mathlib submodule at `lean_lang/mathlib` if you want it
- Bend2: not required
- C#: not required

## Desktop VM
```bash
cd toplethos_lang/cpp_vm
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build
./build/pbatch_demo   # parallel square-map test
```
