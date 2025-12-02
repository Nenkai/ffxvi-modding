---
icon: material/window-restore
---

!!! warning

    This hasn't been released yet sadly. FF16Framework's ImGui hook has hit a roadblock where it crashes with Frame Gen & other overlays that hijacks the DX12 swapchain. [Please contribute if you think you can solve it](https://github.com/Nenkai/FF16Framework/tree/imgui).

    It may be wise to take inspiration from REFramework.

# :material-window-restore: ImGui Overlay API

The framework exposes a ImGui overlay for use by other mods. 

While ImGui is pretty straightforward to use, here are some guides to get started:

* [Interactive Manual/API Reference](https://pthom.github.io/imgui_manual_online/manual/imgui_manual.html)

### Quick Guide

1. Grab `IImGuiSupport`:
```csharp
_imGuiSupport = _modLoader.GetController<IImGuiSupport>();
if (!_imGuiSupport.TryGetTarget(out IImGuiSupport imGuiSupport))
{
    _logger.WriteLine($"[{_modConfig.ModId}] Could not get IImGuiSupport.");
    return;
}
```

2. Inherit from `IImGuiComponent`:
```csharp
public class MyImGuiComponent : IImGuiComponent
{
    // If this is enabled, this will also render while the ImGui overlay is currently hidden
    public bool IsOverlay => false;

    public void RenderMenu(IImGui imgui)
    {
        // Write code to render menu entries here.
        // By default, FF16Framework will render a top menu bar which you can add elements to.
        if (imgui.BeginMenu("MyModName"))
        {
            imgui.MenuItem("Menu Item 1");
            imgui.MenuItem("Menu Item 2");
            imgui.MenuItem("Menu Item 3");

            imgui.EndMenu();
        }
    }

    public void Render(IImGuiSupport imguiSupport, IImGui imgui)
    {
        // Insert code to render anything here.
        if (imgui.Begin("MyWindow", ref _windowOpen, ImGuiWindowFlags.ImGuiWindowFlags_None))
        {
            imgui.Text("Hello World!");
        }

        imgui.End();
    }
}
```

3. Register your component to the ImGui system:
```csharp
// category is the top menu entry which this component will render menu items to.
// name is only used for sorting purposes.
// If your component needs to render a menu, it should always render a sub-group, for clarity.
// Example:
// Tools
// -> MyModName <- This is where RenderMenu starts.
//   -> Menu Item 1
//   -> Menu Item 2
//   -> Menu Item 3
imguiSupport.AddComponent(new PhotoModeMenu(), category: "Tools", name: "MyModName");
```

!!! warning

    The user may choose to not load ImGui based on the framework settings. If you are running logic that needs to run depending on the overlay, ensure to check that `ImGuiSupport.IsOverlayLoaded` is `true`.

That's all you should needed to render something on screen.

<figure markdown>
  ![Image title](imgui_api_menu.jpg){ width="600" }
</figure>

### :material-image: Textures/Images

If you need to render textures, you should:

* Grab a `IImGuiTextureManager` instance
* Pass it to your component. On `Render`, load the texture using `IImGuiTextureManager.LoadImage`. Make sure to only do this once and not every frame!
* Pass the newly added image's `TexId` to `IImGui.Image`, etc.
* Make sure to dispose of these textures when you don't need to use them anymore (closing window, etc).

---

## :material-information-slab-box: Bindings Details

The ImGui bindings have been built using a fork of [dear-bindings](https://github.com/Nenkai/dear_bindings) with the following configuration:

* Built with Freetype (and PlutoSVG for svg font/emoji support)
* DX9/11/12 backend support
* Compiled as Release, with asserts enabled

The bindings have been generated using [ImGuiInterfaceGenerator](https://github.com/Nenkai/FF16Framework/tree/imgui/ImGuiInterfaceGenerator), which works by massaging the output of [ClangSharpPInvokeGenerator](https://github.com/dotnet/ClangSharp) into an interface (for Reloaded and mods), and the implementation/actual bindings for the framework.

### Why new bindings? Why not use [ImGuiNet](https://github.com/ImGuiNET/ImGui.NET) or [Hexa.NET.ImGui](https://github.com/HexaEngine/Hexa.NET.ImGui)?

The goal was to expose ImGui to other mods. That implies using Reloaded-II's [IExports](https://reloaded-project.github.io/Reloaded-II/DependencyInjection_Publisher/) in order to export ImGui itself which meant interfacing nearly the entirety of it. The final output consists of really three files:

* `IImGui.cs`, which is what is exported through Reloaded-II
* `ImGui.cs`, which is the implementation for the interface that sits with the framework
* `ImGuiMethods.cs`, which holds all the native structs and methods used for interop between the framework and ImGui.

On top of this, updating ImGui without breakage would be severely compromised without interfacing; structures would break across breaking changes from upstream ImGui.

What was also considered is:

* Allowing mods to use their own ImGui instance: but judged as too much hassle and possibly too performance consuming.
* Provide a custom api for some interface handling, but ultimately too limiting for mod makers

The current way is not without its flaws, but it should be reasonably feasible to fill interfaces (and provide polyfills if needed) if ImGui is updated in the future. It does require bindings to be diffed and may still be a lot of work though.

---

## :material-hammer-wrench: Building Bindings/Interface

!!! note
    You only need this if you intend to maintain the bindings.

### Step 1: C Bindings

1. Clone [`imgui`](https://github.com/ocornut/imgui) to own folder. Then `git checkout` a specific tag, such as the latest **docking** tag i.e `v1.92.5-docking`
2. Clone [dear-bindings](https://github.com/Nenkai/dear_bindings) (fork) to own folder, NEXT TO imgui. Important!
    * You may need to rebase if you are updating bindings.
3. Install python/requirements for dear-bindings
4. Run `BuildAllBindings.bat`
5. Open `examples/Examples.sln`. The one project we will be editing is **ImGuiLib**.
6. Install vcpkg. Nowadays Visual Studio has an install option for it, which may be default too.
7. Enable vcpkg. Open `Developer Command Prompt for VS` with Administrator permissions, and run `vcpkg integrate install`.
    * To be sure, ImGuiLib properties > vcpkg -> Use Vcpkg Manifest should be on Yes
8. (Hack) remove `extern` for `cImGui_ImplWin32_WndProcHandler` in `dcimgui_impl_win32.h` such that it looks like this:
```cpp
CIMGUI_IMPL_API LRESULT cImGui_ImplWin32_WndProcHandler(HWND hWnd, UINT msg, WPARAM wParam, LPARAM lParam);
```
9. Compile as Release (only ImGuiLib!). You should get `ImGuiLib.dll` and `ImGuiLib.pdb`.

!!! warning

    You may also need to adjust hardcoded include paths I left in for plutosvg because I couldn't get Visual Studio/vcpkg to detect plutosvg as it should.

### Step 2: C# Bindings

1. Install ClangSharpPInvokeGenerator with `dotnet tool install --global ClangSharpPInvokeGenerator --version 20.1.2`
2. Run `generate_dotnet_bindings.bat`.

    !!! note
        * You need to add `#include <Windows.h>` above `CIMGUI_IMPL_API LRESULT cImGui_ImplWin32_WndProcHandler(HWND hWnd, UINT msg, WPARAM wParam, LPARAM lParam);`     temporarily in `dcimgui_impl_win32.h`
        * And `#include <d3d11.h>` to `dcimgui_impl_dx11.h` so that the bindings generation works.

3. The `generated` folder will have `.cs` files with bindings once done.

### Step 3: ImGuiInterfaceGenerator

The framework has a `ImGuiInterfaceGenerator` project. Compile and run it, the first argument to the folder should be the path to the `generated` folder.

Once you run it, you will have `ImGui.cs`, `IImGui.cs` and `ImGuiMethods.cs` files in that project's `generated` folder. They will be in their distinct folders ready to copy to the actual framework folder.

If you are updating bindings you may need to diff changes and provide polyfills if needed.

Copy all the `.dll`+`.pdb` files created previously to `FF16Framework.Native.Binaries`. Update licenses if needed.