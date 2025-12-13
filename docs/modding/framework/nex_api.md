---
icon: material/microsoft-excel
---

# :material-microsoft-excel: Nex API

The [Nex](../../tutorials/nex/nxd_editing.md) API/Interface lets you edit nex tables while the game is running.

!!! note

    The [FF16Tools.Files](https://github.com/Nenkai/FF16Tools/) NuGet Package is required to get the schemas necessary to be able to read rows.

First, grab a `INextExcelDBApiManagedV2`:
```csharp
_nexApi = _modLoader.GetController<INextExcelDBApiManagedV2>();
if (!_nexApi.TryGetTarget(out INextExcelDBApiManagedV2 nextExcelDBApi))
{
    _logger.WriteLine($"[{_modConfig.ModId}] Could not get INextExcelDBApi.");
    return;
}

```

Then, subscribe to an event when the game has loaded the nex database:
```csharp
nextExcelDBApi.OnNexLoaded += NextExcelDBApi_OnNexLoaded;
```

You can use this to apply nex changes immediately once the event fires.

!!! warning
    Always ensure that the database is initialized before attempting to do any changes (especially if you are applying changes again from a configuration change through `ConfigurationUpdated`).

```csharp
if (!nextExcelDBApi.Initialized)
    return;
```

### Basic usage
```csharp
// Grab a table. (note: NexTableIds is only relevant to FFXVI)
// You can pass a raw number. Table ids are defined in root.nxl in each respective game
INexTable? photoTable = nextExcelDBApi.GetTable(NexTableIds.photocameraparam);
if (photoTable is null)
{
    // Handle error
}

// Get a specific row
INexRow? row = photoTable.GetRow(7);
if (row is null)
{
    // Handle error
}

// Iterate through rows/get keys
uint numSets = photoTable.GetNumSets();
for (uint i = 0; i < numSets; i++)
{
    uint key1 = photoTable.GetMainKeyByIndex(i);
    // ...
}

// Double keyed (example)
INexTable? gamemap = nextExcelDBApi.GetTable(NexTableIds.gamemap);
uint numSubSets = gamemap.GetSubSetCount(200000);
IReadOnlyList<NexSubSetInfo> allSubSets = photoTable.GetSubSetInfos(200000);
for (uint i = 0; i < numSubSets; i++)
{
    NexSubSetInfo? subSetInfo = gamemap.GetSubSetInfoByIndex(200000, i);
    if (subSetInfo is null)
    {
        // Handle error
    }
}

// Manipulate/Fetch row
NexTableLayout layout = TableMappingReader.ReadTableLayout("photocameraparam", ...); // From FF16Tools.Files

float collisionSphereRadius = row.GetSingle((uint)layout.Columns["CollisionSphereRadius"].Offset);
row.SetSingle((uint)layout.Columns["CollisionSphereRadius"].Offset, 133.7f);
```