---
icon: material/package
---

# :material-package: Pack - `.pac`

The pack is the main holder for the data in FINAL FANTASY XVI. It is custom made for FFXVI and designed around [DirectStorage](https://github.com/microsoft/DirectStorage).

Packs are split per game folder in general. You can find a list [here](../asset_paths.md).

The game will always try to load a `.diff` variant file for every single pack. File entries present in there will be appended on top of the base package.

* [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_pac_PACK.bt)
* [Reference Implementation (FF16Tools, C#)](https://github.com/Nenkai/FF16Tools)

## Behavior

The game holds a map of all the files in the game, which means that every single pack's entries are merged into this map (meaning it is possible to add any sort of content in any pack).

Packs can contain a "general directory name" in its header, meaning that every file is a sub-directory of it. For instance `0007` has it as `nxd`, so a file entry such as `access.nxd` maps to `nxd/access.nxd`.

The pack itself may contain nested packs such as the ones in the `chara/cXXXX/pack` folders. When these do get loaded, files in it will also get merged into this one unique map, which is the reason why all paths under the nested pack follows the same global paths.

!!! example

    `chara/c7045/pack/c7045.pac` contains `animation/chara/c7045/skeleton/body/body.skl`.

    Instead of being mounted as `chara/c7045/pack/animation/chara/c7045/skeleton/body/body.skl`

    It will be mounted as `animation/chara/c7045/skeleton/body/body.skl` due to pack merging.

### Data Chunks

Packs can store compressed [GDeflate](https://github.com/microsoft/DirectStorage/blob/main/GDeflate/README.md) chunks that can house multiple files. The rules are:

* Files that are not compressed are stored raw.
* Files that are smaller than `0x100000` (1Mb) are stored in shared chunks - chunks that contain multiple chunks. Shared chunks are not bigger than `0x400000` (4 Megabytes) **when decompressed**.
* Files that are bigger than `0x2000000` (32Mb) are stored in multiple unique chunks. These chunks are split into `0x80000` (512Kb) parts **when decompressed**.

---

## Header

```c
struct
{
    uint64_t Magic // PACK
    uint32_t HeaderSize; // Size of the Header/TOC
    uint32_t NumFiles;
    bool UsesChunks;
    bool Encrypted; // If true, DirectoryName and the string table is encrypted.
    uint16_t NumChunks;
    uint64_t PackSize; // Total Size
    
    // Important: Main directory of the pack. Any file will be a sub-file of this.
    uint8_t DirectoryName[0x100];

    uint64_t ChunkTableOffset; // To DirectStorageSharedChunkInfo[]
    uint64_t StringTableOffset;
    uint64_t StringTableSize;
    uint8_t Padding[0x2D0]; // Padding until 0x400
} PackHeader; // size: 0x400

```

### File Infos
Starting at `0x400`: array of `FileInfo`

```c
typedef enum
{
    None,
    UseSpecificChunk, // File is stored in a single GDeflate chunk
    UseMultipleChunks, // File is stored within multiple GDeflate chunks
    UseSharedChunk // File is stored in a chunk where multiple files reside
} FileChunkedCompressionFlags;

struct
{
    uint32_t CompressedFileSize <format=hex>;
    bool IsCompressed;
    FileChunkedCompressionFlags ChunkedCompressionFlags; // uint8
    uint16_t Empty;
    uint64_t DecompressedFileSize <format=hex>;
    // To GDeflate compressed data (if compressed). 
    // If UseMultipleChunks is used, points to a header (see DirectStorageMultiChunkHeader)
    uint64_t DataOffset; 
    uint64_t ChunkDefOffsetOrPathLength; // This is path length instead if the file is empty. Used for nested packs.
    uint64_t FileNameOffset;
    uint32_t FileNameHash; // FNV Hash, NOT FNV1A
    uint32_t CRC32Checksum; // Of the decompressed data
    uint32_t IsEmpty;
    uint32_t ChunkHeaderSize <format=hex>; // 0x18 if UseSharedChunk, variable if UseMultipleChunks
} FileInfo; // size: 0x48
```

### DirectStorageSharedChunkInfo

Represents a GDeflate-compressed chunk, which houses multiple files.

A shared chunk is never more than `0x400000` in size, and never has files larger than `0x100000`.

This is used by files marked with `FileChunkedCompressionFlags.UseSharedChunk`.

```c
struct
{
    uint64_t DataOffset;
    uint32_t CompressedChunkSize;
    uint32_t ChunkDecompressedSize;
    uint32_t Empty;
    uint16_t ChunkIndex;
    uint16_t NumFilesInChunk;
} DirectStorageSharedChunkInfo; // size: 0x18
```

### DirectStorageMultiChunkHeader

Multiple chunks for a single file is used when a file is at least `0x2000000` (32Mb).

```c
struct
{
    uint32_t NumChunks;
    uint32_t LastChunkSize; // High 8 bits may be for something different?
    uint32_t ChunkOffsets[NumChunks];
} DirectStorageMultiChunkHeader;
```

---

## Decryption

```csharp
public const ulong XOR_KEY = 0x49D18FC870F3824E;

public static void CryptHeaderPart(Span<byte> data)
{
    Span<byte> cur = data;
    while (cur.Length >= 8)
    {
        MemoryMarshal.Cast<byte, ulong>(cur)[0] ^= XOR_KEY;
        cur = cur[8..];
    }

    if (cur.Length >= 4)
    {
        MemoryMarshal.Cast<byte, uint>(cur)[0] ^= (uint)(XOR_KEY & 0xFFFFFFFF);
        cur = cur[4..];
    }

    if (cur.Length >= 2)
    {
        MemoryMarshal.Cast<byte, ushort>(cur)[0] ^= (ushort)(XOR_KEY & 0xFFFF);
        cur = cur[2..];
    }

    if (cur.Length >= 1)
        cur[0] ^= (byte)(XOR_KEY & 0xFF);
}
```