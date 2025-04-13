---
icon: material/bug
---

# :material-bug: Debugging

FFXVI has a rudimentary anti-debugging mechanism (in non-denuvo versions). `IsDebuggerPresent()` is present on the entrypoint and will immediately return if a debugger is attached.

Another anti-debug mechanism is used after the splash screen (which may involve `HeapFlags` detection - needs more research).

## x64dbg

ScyllaHide's Hide from PEB -> `BeingDebugged` and `HeapFlags` is enough to hide the debugger.

## Cheat Engine

Use the VEH debugger. Settings -> Debugger Options -> Use VEH debugger. This also works on Denuvo protected versions of the game.