---
icon: material/file-excel-box
---

# :material-file-excel-box: Nex - `.nxd`

Originally in Excel form, Nex (Next ExcelDB) are database table files. SQEX converts them into a binary format (`.nxd`) - sister of FF14's `.exd` but with less metadata and little endian.

These files are located in the `nxd` folder. (`0007` packs).

Unlike `exd`, there are **no column metadata** whatsoever. No names, no cell fields. All had to be manually mapped.

* [.exd Documentation](https://xiv.dev/game-data/file-formats/excel#excel-data-.exd) (FF14)
* [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_nxd_NXDF.bt)
* [Reference Implementation (FF16Tools, C#)](https://github.com/Nenkai/FF16Tools)
* [Table Layouts](https://github.com/Nenkai/FF16Tools/tree/master/FF16Tools.Files/Nex/Layouts)
* [Database Table Editing](../../tutorials/nex/nxd_editing.md)

*Additionally*, row data itself can contain nested structures or arrays.

!!! note

    Ids are also always ordered due to binary search use.


## Header

```c
struct
{
    uint32_t magic <format=hex>; // 'NXDF'
    uint32_t version; // 1
    enum // uint8_t
    {
        NEX_ROWTYPE_SINGLEKEYED = 1, // 1 key
        NEX_ROWTYPE_DOUBLEKEYED = 2, // 2 keys
        NEX_ROWTYPE_TRIPLEKEYED = 3, // 3 keys
    } type;
    
    enum // uint8_t
    {
        NEX_SINGLEKEYED_UNLOCALIZED = 1,
        NEX_SINGLEKEYED_LOCALIZED = 2,
        NEX_DOUBLEKEYED_UNLOCALIZED = 3,
        NEX_DOUBLEKEYED_LOCALIZED = 4,
        NEX_TRIPLEKEYED_ROWS_UNLOCALIZED = 5,
        NEX_TRIPLEKEYED_ROWS_LOCALIZED = 6
    } category;
    
    // Determines whether to use the baseRowId for searching.
    // if baseRowId is 1, searching for row id 0 will return the first row.
    bool usesBaseRowId; 
    uint8_t _reserved1_;
    uint32_t baseRowId;
    uint32_t _reserved2_[0x4];
} NexDataFileHeader; // size: 0x20
```

Following the main header, another header follows depending on the type of table.

### Type 1 (Single-Keyed)

Simple rows with only one key.

```c
struct
{
    int32_t rowInfosOffset; // Offset to a list of row infos for each row
    uint32_t numRows;
} NexSingleKeyedTableHeader;
```

```c
struct
{
    uint32_t rowID;
    int32_t rowDataOffset; // Relative to start of row info.
} NexSingleKeyedTableRowInfo;
```

---

### Type 2 (Double-keyed)

Rows, with two keys.

#### NexDoubleKeyedTableHeader
```c
struct
{
    uint32_t thisHeaderSize; // Also used as an offset relative to this for NexDoubleKeyedSetInfo[].
    uint32_t setCount; // Number of sets in this table.
    uint32_t reserved;
    int32_t rowsInfoOffset; // Points to another list of the data for each row (not row set).
    uint32_t totalRowCount; // Total number of rows in this table.
} NexDoubleKeyedTableHeader;
```

##### NexDoubleKeyedSetInfo
```c
struct
{
    uint32_t key; // main row id/set id.
    int32_t rowInfosOffset; // Offset to NexDoubleKeyedRowInfo[], relative to this structure.
    uint32_t arrayLength; // Number of rows for this set.
} NexDoubleKeyedSetInfo;
```

##### NexDoubleKeyedRowInfo
```c
struct
{
    uint32_t key;
    uint32_t key2;
    int32_t rowDataOffset; // Relative to this structure.
} NexDoubleKeyedRowInfo;
```

##### NexRowInfo
```c
struct
{
    uint32_t key;
    uint32_t key2; // array index, or key2.
    int32_t rowDataOffset; // Relative to this structure. May be negative (reverse offset).
} NexRowInfo;
```

### Type 3 (Triple-Keyed Sets)

Rows sets, with three keys.

#### NexTripleKeyedTableHeader
```c
struct
{
    uint32_t thisHeaderSize;  // Also used as an offset relative to this for NexTripleKeyedSetInfo[].
    uint32_t count; // Number of triple-keyed sets in this table.
    int32_t rowInfoOffset;
    int32_t rowsInfoOffset; // Points to another list of the data for each row.
    uint32_t totalRowCount; // Total number of rows in this table.
} NexTripleKeyedTableHeader;
```

##### NexTripleKeyedSetInfo
```c
struct
{
    uint32_t key; // Main row id.
    uint32_t subRowSetInfoOffset; // Offset to NexTripleKeyedSubSetInfo[], relative to this structure.
    uint32_t numSubKeys; // Number of sub row keys.
    uint32_t unkOffset; // Unknown, never used.
    uint32_t unkAlways0; // Unknown, possible count for above, never used.
} NexTripleKeyedSetInfo;
```

##### NexTripleKeyedSubSetInfo
```c
struct
{
    uint32_t key2; // or key2.
    uint32_t unkOffset; // Unknown, never used.
    uint32_t unkAlways0; // Unknown, possible count for above, never used.
    int32_t rowInfosOffset; // Offset to NexTripleKeyedRowInfo[], relative.
    uint32_t numRows; // Number of rows for this subset.
} NexTripleKeyedSubSetInfo;
```

##### NexTripleKeyedRowInfo
```c
struct
{
    uint32_t key;
    uint32_t key2; // or key2.
    uint32_t key3; // array index, or key3.
    uint32_t unkAlways0; // Unknown, never used.
    int32_t rowDataOffset; // Relative to this structure. May be negative (reverse offset).
} NexRowInfo;
```