# RustDeskPL build

Build an independent Windows x64 RustDesk client named **RustDeskPL** alongside a standard RustDesk installation.

- Upstream: [RustDesk 1.5.0](https://github.com/rustdesk/rustdesk/tree/fada664df7a294d1d1a9ca3e7cd3637069122f17), pinned to commit `fada664df7a294d1d1a9ca3e7cd3637069122f17`.
- Only source change: the default `APP_NAME` in `libs/hbb_common/src/config.rs` becomes `RustDeskPL`.
- The Windows launcher is packaged as `RustDeskPL.exe`; keep its DLLs and `data` directory together.
- A Windows build check loads the compiled DLL and verifies the application identity before uploading the artifact.
- The resulting client is an unsigned test build. Concurrent service operation, server configuration isolation, UAC, and unattended access after reboot still require a pilot on Windows.
- No passwords, server keys, or existing client settings are embedded. No client is installed automatically.

## Build

Open **Actions → Build RustDeskPL 1.5.0 for Windows x64**. The initial workflow commit starts a build; further builds can be started with **Run workflow**.

After both jobs succeed, download **RustDeskPL-1.5.0-windows-x64** from that run. If a job fails, inspect its first failed step.

Source licensing is unchanged; the distribution includes upstream `LICENCE`. Optional printer/virtual-display driver bundles are not included in this pilot package.
