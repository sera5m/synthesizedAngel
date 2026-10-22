# Build dependencies

## Required
- C++20 minimum, C++26 preferred
  - CMake ≥ 3.20
  - Compiler: GCC ≥ 12 / Clang ≥ 15 (C++20); newer for C++26
  - Threads (pthread) — used by the parallel batch queue
- Toplethos language: submodule at `toplethos_lang/`
- Toplethos IDE: submodule at `toplethos_ide/` (graph window + VS Code extension)
  ```bash
  git submodule update --init toplethos_lang toplethos_ide
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

## Graph IDE
```bash
cd toplethos_ide
python3 toplethos_ide.py
```
VS Code extension install is in `toplethos_ide/vscode-toplethos/README.md`.
