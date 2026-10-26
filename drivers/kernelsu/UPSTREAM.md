# KernelSU-Next in-tree import

- Repository: https://github.com/KernelSU-Next/KernelSU-Next.git
- Branch: `dev`
- Revision: `b427a3f9c2421a443f961007bfce66b25486643f`
- Nearest release tag: `v3.4.2` (this import includes later dev changes)
- Upstream commit count: `3405`; reported kernel version: `33405`

The upstream `kernel/` directory is imported here. Its `include/uapi` symlink
is materialized from the upstream top-level `uapi/` directory so this import
is self-contained. The kernel driver retains its upstream GPL-2.0-only
license. The imported top-level UAPI headers retain the upstream repository's
licensing; its GPLv3 license text is provided in `include/uapi/COPYING`.

Local integration enables `CONFIG_KSU=y` in Pong's vendor config and wires
the driver into `drivers/Kconfig` and `drivers/Makefile`. The Kbuild includes
`upstream-version.mk` to preserve version metadata without a nested Git repo
or a build-time network fetch. Update that file when importing a new revision.

This branch provides its own syscall/kprobe integration. Do not apply the
legacy manual exec/read/stat/input hooks on top of it. Debug mode and
manager/policy disabling options remain off by default. No SUSFS patch set
is applied to the surrounding kernel.
