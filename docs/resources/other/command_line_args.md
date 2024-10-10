---
icon: octicons/terminal-16
---

# :octicons-terminal-16: Command Line Arguments

The game has a few undocumented command line arguments. Mostly DirectStorage related.

## Working Arguments

These are confirmed read/used parameters.

### `/memory_limit <gbs>`
Sets the memory limit in GBs.

### `/windowtopmost`
Makes the game be on top of all other programs.

### `/razor_gpu_friendly`
Razer chroma related

### `/razor_cpu_friendly`
Razer chroma related

### `/disable_file_cache`

### `/disable_direct_device`
Sets something directstorage related - directx device/resource transfer related?

### `/disable_direct_destination`
Sets something directstorage related - directx device/resource transfer related?

### `/disable_directstorage`
Unclear whether it actually disables it, seems to be the case.

### `/buildin_cpu_decompression_threads <number>`
Sets [DSTORAGE_CONFIGURATION1.NumBuiltInCpuDecompressionThreads](https://learn.microsoft.com/en-us/windows/win32/dstorage/dstorage/ns-dstorage-dstorage_configuration1)

### `/disable_gpu_decompression_metacommand`
Sets [DSTORAGE_CONFIGURATION1.DisableGpuDecompressionMetacommand](https://learn.microsoft.com/en-us/windows/win32/dstorage/dstorage/ns-dstorage-dstorage_configuration1)

### `/disable_gpu_decompression`
Sets [DSTORAGE_CONFIGURATION1.DisableGpuDecompression](https://learn.microsoft.com/en-us/windows/win32/dstorage/dstorage/ns-dstorage-dstorage_configuration1)

### `/enable_builtin_cpu_decompression`
Enables use of [DSTORAGE_CONFIGURATION1.NumBuiltInCpuDecompressionThreads](https://learn.microsoft.com/en-us/windows/win32/dstorage/dstorage/ns-dstorage-dstorage_configuration1)

### `/disable_file_buffering`
Won't set [DSTORAGE_CONFIGURATION1.ForceFileBuffering](https://learn.microsoft.com/en-us/windows/win32/dstorage/dstorage/ns-dstorage-dstorage_configuration1) and [DSTORAGE_CONFIGURATION1.DisableBypassIO](https://learn.microsoft.com/en-us/windows/win32/dstorage/dstorage/ns-dstorage-dstorage_configuration1)

### `/ignore_config`
Ignore loading system save files aka system-save-data and config.xml

### `/enable_memory_save`

## Stubbed

Game parses these, but does not use them (stripped by release build).

* `/exceptionoff` (possibly)
* `/disable_tty`
* `/cmd`
* `/console`