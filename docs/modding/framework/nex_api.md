---
icon: material/microsoft-excel
---

# :material-microsoft-excel: Nex API

The [Nex](../../tutorials/nex/nxd_editing.md) API/Interface lets you edit nex tables while the game is running.

!!! note

    The [FF16Tools.Files](https://github.com/Nenkai/FF16Tools/) NuGet Package is required to get the schemas necessary to be able to read rows.

First, grab a `INextExcelDBApiManaged`:
```csharp
_nexApi = _modLoader.GetController<INextExcelDBApiManaged>();
if (!_nexApi.TryGetTarget(out INextExcelDBApiManaged nextExcelDBApi))
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