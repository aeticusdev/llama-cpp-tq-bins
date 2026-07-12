# llamacompiler

GitHub Actions workflows to compile [llama-cpp-turboquant](https://github.com/TheTom/llama-cpp-turboquant) for every target.

## What it builds

| Workflow | Trigger | Jobs |
|----------|---------|------|
| `build-linux-multiarch` | push/PR/schedule/manual | 4 jobs: x86_64 cpu+vulkan, arm64 cpu+vulkan, x86 cpu, arm32 cpu |
| `build-windows-multiarch` | push/PR/schedule/manual | 3 jobs: x86_64 cpu+vulkan, arm64 cpu, x86 cpu |
| `tqp-multiarch-release` | tag `tqp-v*` / manual | 10 jobs: all above + cuda (win+linux) |

## Artifacts

- Linux/macOS → `.tar.gz`
- Windows → `.zip`

Naming: `turboquant-plus-$TAG-$PLATFORM-$BACKEND.tar.gz|zip`

## Tags

Push `tqp-vX.Y.Z` → auto release.

Manual: Actions tab → `TurboQuant+ Multi-Arch Release` → pick ref + tag.

## Caveats

- x86 Linux / arm32 Linux: cross-compile. No test run.
- Windows x86/arm64: cross-compile via LLVM toolchain.
- Vulkan builds need Vulkan SDK at runtime.


## Schedule

CI runs every Sunday 06:00 UTC (weekly heartbeat).
