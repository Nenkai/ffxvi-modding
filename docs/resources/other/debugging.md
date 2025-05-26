---
icon: material/bug
---

# :material-bug: Debugging

FFXVI has a rudimentary anti-debugging mechanism.

There's are three distinct anti-debugging checks:

* App entrypoint has a `IsDebuggerPresent` check and will immediately return if `true`
* App update loop (which returns whether false on whether to end the game loop) has `IsDebuggerPresent`, if flagged, the function returns `false` and the game will shut down.
* App update loop capturer checks after above check, it checks if the following module handles are loaded in the process and does the same flagging if `true`: 
    - [Pix](https://devblogs.microsoft.com/pix/) (`winPixGpuCapturer.dll`)
    - [Nvidia Nsight Graphics](https://developer.nvidia.com/nsight-graphics) (`Nvda.Graphics.Interception.dll`)
    - [Intel Graphics Performance Analyzers](https://www.intel.com/content/www/us/en/developer/tools/graphics-performance-analyzers/overview.html) (`capture-x64.dll`/`d3d12-state-tracker-x64.dll`) 
    - [RenderDoc](https://renderdoc.org/) (`renderdoc.dll`) + GUID check with `d3d12Device->QueryInterface({ 0xa7aa6116, 0x9c8d, 0x4bba, { 0x90, 0x83, 0xb4, 0xd8, 0x16, 0xb7, 0x1b, 0x78 } })`

!!! tip

    The mod loader as of 1.2.0 disarms the anti-debug checks.

## Bypassing

Use the mod loader to disable anti-debug checks.

### x64dbg

ScyllaHide's Hide from PEB -> `BeingDebugged` and `HeapFlags` is enough to hide the debugger. 

!!! warning

    Without `HeapFlags`, the game appears to get stuck without showing the main window for some reason when starting rather than attaching. 
    
    **It may need more research.**

### Cheat Engine

Use the VEH debugger. Settings -> Debugger Options -> Use VEH debugger. This also works on Denuvo protected versions of the game.

### IDA

Use the mod loader and attach. 

!!! warning
    
    Starting the process and nopping `IsDebuggerPresent` causes the same issue where the game gets stuck without showing the main window.