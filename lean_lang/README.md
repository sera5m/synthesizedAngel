# lean_lang

Lean 4 specs and proofs.

## Setup
```bash
elan toolchain install stable
elan default stable
```

mathlib is available as a submodule at `lean_lang/mathlib` if needed:
```bash
git submodule update --init lean_lang/mathlib
```

Not required for the core simulator runtime.
