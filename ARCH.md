# Arch install

Two layers. The first builds and runs the project. The second is the desktop you actually work in.

## Required

```bash
sudo pacman -S --needed \
  base-devel git cmake ninja pkgconf \
  gcc clang gdb \
  python python-pip \
  python-gobject gtk4 gtksourceview5 \
  python-pyserial python-matplotlib
```

| package | why |
|---|---|
| `base-devel` | `make`, headers, the usual C toolchain meta |
| `gcc` | C and C++20. Arch's current gcc is new enough for the C++20 floor |
| `clang` | second compiler; closer to C++26 as it lands |
| `cmake` `ninja` | desktop VM build |
| `pkgconf` | finding gtk / gobject when something links them |
| `gdb` | when a sector kernel faults |
| `python` `python-gobject` `gtk4` | current Toplethos IDE |
| `gtksourceview5` | real text widget if the GTK editor grows a node tile |
| `python-pyserial` `python-matplotlib` | existing IDE deps (UART, plots) |

C++26 is not a separate package. Use whatever `gcc` / `clang` Arch is shipping and gate new syntax with feature-test macros. Do not pin an old gcc.

Lean is optional and should come from elan, not the compiler source:

```bash
curl https://elan.lean-lang.org/elan-init.sh -sSf | sh
elan toolchain install stable
```

`lean4` also exists in the AUR (`lean4-bin`). Prefer elan so mathlib and the toolchain stay in lockstep.

## Desktop, recommended

```bash
# AUR helper assumed (yay or paru)
yay -S --needed strata-bin visual-studio-code-bin
```

| package | why |
|---|---|
| `strata-bin` | keyboard-first GTK4 file manager. Already on GTK4, same stack as the IDE |
| `visual-studio-code-bin` | host for the graph extension. Official build, marketplace works |

`code` (Code - OSS, in `[extra]`) is fine if you do not want the Microsoft binary. Marketplace extensions are harder there. For this project use `visual-studio-code-bin`.

Node is only required once the VS Code extension exists:

```bash
sudo pacman -S --needed nodejs npm
```

## Not required

- C# / `dotnet-sdk`
- Bend
- CUDA toolkit. The batch queue is CPU threads until a real GPU kernel exists. Add `cuda` then, not now.
- A second editor. One of VS Code or the GTK IDE, not both as primary.

## After packages

```bash
git clone --recurse-submodules https://github.com/sera5m/synthesizedAngel.git
cd synthesizedAngel
git submodule update --init toplethos_lang
cd toplethos_lang/cpp_vm
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
./build/pbatch_demo
```
