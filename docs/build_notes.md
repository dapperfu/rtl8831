# RTL8851bu build notes

## Compiler version notice

When building the driver as an out-of-tree kernel module, you may see:

```
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-13 (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
  You are using:           gcc-13 (Ubuntu 13.3.0-6ubuntu2~24.04.1) 13.3.0
```

This is expected when the system default `gcc` (or the one in your `PATH`) is a slightly different build than the compiler used to build the running kernel (e.g. different patch level). It can be ignored for normal development; the module will build and load. To match the kernel compiler exactly, use the same compiler the kernel was built with (often available as `x86_64-linux-gnu-gcc-13` on Debian/Ubuntu).

## Build warnings baseline

See `docs/build_warnings_baseline.txt` for a list of warning locations captured from a full build. The driver build uses `-Wno-missing-prototypes` so that the build completes without warnings; that file documents where prototypes can be added for a future strict build.
