---
icon: material/api
---

# Mod Manager API

!!! note
    This page is intended for programmers with knowledge in C#.

As of `ff16.utility.modloader` 1.1.3, a modding interface/API is now exposed. 

This API can be leveraged to create file mods through your own C# code.

## Setting Up

1. [Setup a development environment](https://reloaded-project.github.io/Reloaded-II/DevelopmentEnvironmentSetup/) for Reloaded-II mods.
2. [Create a New Project](https://reloaded-project.github.io/Reloaded-II/ProjectSetup/) using the Reloaded II Mod template.
3. Add the [`ff16.utility.modloader.Interfaces`](https://www.nuget.org/packages/ff16.utility.modloader.Interfaces) NuGet package to your project.
4. Add `ff16.utility.modloader` to `ModDependencies` in **ModConfig.json**.

## Usage

Refer to the [Dependencies Consumption documentation](https://reloaded-project.github.io/Reloaded-II/DependencyInjection_Consumer/) to understand the concept behind shared libraries.

In your mod's constructor, grab a reference to `IFF16ModPackManager`:

```csharp
// Fetch IFF16ModPackManager to add files
_modLoader.GetController<IFF16ModPackManager>()?.TryGetTarget(out IFF16ModPackManager modPackManager!);

// Adding a new modded file
modPackManager.AddModdedFile(_modConfig.ModId, "path to mod's data directory", "game path");

// Removing a modded file
if (modPackManager.RemoveModdedFile("game path"))
{
    // File was removed
}
```

Changes will be applied to pack files once the mod loader has loaded all other mods, including yours.