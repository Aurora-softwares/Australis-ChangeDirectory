# Australis Change Directory prototype

## Current status

The current source prints `Hello, World!` and does not change directories.

`ChangeDirectory.hyproj` builds `change-directory.exec`. The Australis OS aggregate includes
this project and installs the executable at `/Bin/change-directory.exec` in the read-only
HyFS 2 boot image. Run it by its bare name `/Bin/` through the current
recovery shell's `PATH`, or use `run /Bin/change-directory.exec`.

## Planned direction

`cd` belongs in the shell because a child executable cannot change its parent shell's working directory. This project must be retired or repurposed as a path-inspection utility; it is not the planned `cd` implementation.

Build this checkout with:

```bash
mkdir -p build
hy build ChangeDirectory.hyproj -o build/change-directory.exec
```

AUEX `.exec` files currently run in the checked interpreter. Native ring-3
processes and a normal userland shell are later milestones. The boot root is
read-only; writable application data belongs on the separate `/data` volume.
The OS-level build, supported APIs, and packaging rules are described in the
Australis OS `applications/README.md`. This README describes this project's
actual source rather than treating its filename as proof of a finished feature.
